> 🇬🇧 **English** · 🇹🇷 Türkçe sürüm aşağıdadır.

# 3.6.6 · Algorithms for Relational Database — Query and transaction algorithms

## Query execution approach

**Table 12. Use of relational database algorithms in the project**

| Operation | Suitable access / algorithm | Effect on the project |
|---|---|---|
| Q1 patient list | Assignment index + indexed nested-loop join via the Patients PK | Patient information is reached from a small number of assignments. |
| Q2 measurement history | B-tree range scan + equality join with the type table | Patient and time range are narrowed; type/unit are fetched. |
| Q3 task list | Recipient/status index scan + assignment match | Pending tasks are selected by the responsible staff member. |
| Q4 patients without measurements | Anti-join / NOT EXISTS approach | Assigned patients with no matching measurement are obtained. |
| Large equality joins | Hash join; sequential scan may be chosen on small tables | Alternative plans are considered depending on data size. |
| Date ordering | Suitable index order or sort | The ID is the second sort key for records with the same time. |

At course level, B-tree range access is about O(log N + k), a sequential scan O(N), a hash join expected O(N + M) and a general sort O(N log N). N/M are input sizes and k is the number of result rows. These are not timing measurements; PostgreSQL chooses the real plan.

## Transaction checks

In the pseudocode below, the user ID is taken from the session. Writes are done in a single transaction: they are rolled back if a check fails, and success is reported only after commit. The related users are protected with shared locks in ID order and the patient row with a write lock; in the completion operation the message row is locked last with a write lock. Assignment changes follow the same patient lock. Deactivation locks the user row for writing and checks pending tasks addressed to that user. In this way K24 stays consistent with task creation and completion.

### A · Get patient profile

Input: session user u, patient p. Output: profile or access denied.

```
1. If u is not an active doctor/nurse, deny access.
2. If (p, u) is not in PatientStaff, deny access.
3. Get the basic information of patient p from Patients.
4. Filter Measurements by p; join with type and recording staff.
5. Return measurements in descending observed_at and measurement_id order.
6. Filter messages by p and (sender_id=u or recipient_id=u).
7. Show the profile with basic info, measurements and authorized messages.
```

### B · Record measurement

Input: u, p, type t, value v, observation time. Output: new measurement or rejection.

```
1. Start transaction; take the related user and patient locks.
2. If u is not an active doctor/nurse or is not assigned to p, roll back.
3. Does t exist; is v positive, finite, within limits and at most 2 decimals?
4. Is the observation time after the record time? If invalid, roll back.
5. Insert p, t, u, v, observation and record time into Measurements.
6. Commit; return the new measurement ID.
```

### C · Send task message

Input: sender u, patient p, recipient r, text. Output: Pending message or rejection.

```
1. Start transaction; lock users u and r in ID order,
   then lock patient p.
2. If u is not an active doctor or is not assigned to p, roll back.
3. If r is not an active doctor/nurse, not assigned to p, or r=u, roll back.
4. If the text is empty or longer than 1,000 characters, roll back.
5. Insert p, u, r, text, creation time and Pending into Messages.
   result_text=NULL; completed_at=NULL.
6. Commit; return the message ID.
```

### D · Complete task

Input: session user u, message m, result text. Output: Completed or rejection.

```
1. Start transaction; lock user u.
2. Find message m and its patient; lock the patient, then the message row.
3. Is u an active doctor/nurse, the message recipient and assigned to the patient?
   If any condition fails, roll back.
4. If the status is not Pending or the result is empty/longer than 1,000, roll back.
5. Keep the recipient and Pending conditions in the UPDATE as well.
   status=Completed; result_text=result; completed_at=record time.
6. Commit if exactly one row changed; otherwise roll back.
```

> **Note:** If the same task is completed twice, only the first valid state change is accepted. Locking the patient row is a simple consistency choice for a small project; it serialises concurrent writes for the same patient.

---

> 🇹🇷 **Türkçe**

# 3.6.6 · Algorithms for Relational Database — Sorgu ve işlem algoritmaları

## Sorgu yürütme yaklaşımı

**Tablo 12. İlişkisel veritabanı algoritmalarının projedeki kullanımı**

| İşlem | Uygun erişim / algoritma | Projeye etkisi |
|---|---|---|
| Q1 hasta listesi | Atama indeksi + Patients PK üzerinden indeksli nested-loop join | Az sayıdaki atamadan hasta bilgisine erişilir. |
| Q2 ölçüm geçmişi | B-tree aralık taraması + tür tablosuyla eşitlik join’i | Hasta ve zaman aralığı daraltılır; tür/birim getirilir. |
| Q3 görev listesi | Alıcı/durum indeks taraması + atama eşleştirmesi | Bekleyen görevler sorumlu personele göre seçilir. |
| Q4 ölçümsüz hastalar | Anti-join / NOT EXISTS yaklaşımı | Ölçüm eşleşmesi bulunmayan atanmış hastalar elde edilir. |
| Geniş eşitlik birleştirmeleri | Hash join; küçük tablolarda sequential scan seçilebilir | Veri büyüklüğüne bağlı alternatif planlar değerlendirilir. |
| Tarih sırası | Uygun indeks sırası veya sort | Aynı zamanlı kayıtlarda kimlik ikinci sıralama alanıdır. |

B-tree aralık erişimi ders düzeyinde yaklaşık O(log N + k), ardışık tarama O(N), hash join beklenen O(N + M), genel sıralama O(N log N) olarak değerlendirilir. N/M girdi, k sonuç satırı sayısıdır. Bunlar süre ölçümü değildir; gerçek planı PostgreSQL seçer.

## İşlem kontrolleri

Aşağıdaki sözde kodlarda kullanıcı kimliği oturumdan alınır. Yazmalar tek transaction içinde yapılır: başarısız kontrolde geri alınır, başarı yalnız commit sonrasında bildirilir. İlgili kullanıcılar kimlik sırasıyla paylaşımlı, hasta satırı yazma kilidiyle; tamamlama işleminde son olarak mesaj satırı yazma kilidiyle korunur. Atama değişiklikleri de aynı hasta kilidine uyar. Pasifleştirme kullanıcı satırını yazma kilidiyle koruyup bekleyen alıcı görevlerini kontrol eder. Böylece K24 ile görev oluşturma/tamamlama işlemleri tutarlı kalır.

### A · Hasta profilini getir

Girdi: oturum kullanıcısı u, hasta p. Çıktı: profil veya erişim reddi.

```
1. u aktif doctor/nurse değilse erişimi reddet.
2. PatientStaff içinde (p, u) yoksa erişimi reddet.
3. Patients içinden p hastasının temel bilgilerini al.
4. Measurements’ı p ile süz; tür ve kaydeden personelle birleştir.
5. Ölçümleri observed_at ve measurement_id azalan sırada getir.
6. Mesajları p ve (sender_id=u veya recipient_id=u) ile süz.
7. Temel bilgi, ölçümler ve yetkili mesajlarla profili göster.
```

### B · Ölçüm kaydet

Girdi: u, p, tür t, değer v, gözlem zamanı. Çıktı: yeni ölçüm veya ret.

```
1. Transaction başlat; ilgili kullanıcı ve hasta kilitlerini al.
2. u aktif doctor/nurse değilse veya p hastasına ataması yoksa geri al.
3. t var mı; v pozitif, sonlu, sınır içinde ve en çok 2 ondalıklı mı?
4. Gözlem zamanı kayıt zamanından sonra mı? Hatalıysa geri al.
5. Measurements’a p, t, u, v, gözlem ve kayıt zamanını ekle.
6. Commit yap; oluşturulan ölçüm numarasını döndür.
```

### C · Görev mesajı gönder

Girdi: gönderen u, hasta p, alıcı r, metin. Çıktı: Pending mesaj veya ret.

```
1. Transaction başlat; u ve r kullanıcılarını kimlik sırasıyla,
   ardından p hastasını kilitle.
2. u aktif doktor değilse veya p hastasına atanmamışsa geri al.
3. r aktif doctor/nurse değilse, p ataması yoksa veya r=u ise geri al.
4. Metin boşsa veya 1.000 karakteri aşıyorsa geri al.
5. Messages’a p, u, r, metin, oluşturulma zamanı ve Pending ekle.
   result_text=NULL; completed_at=NULL.
6. Commit yap; mesaj numarasını döndür.
```

### D · Görevi tamamla

Girdi: oturum kullanıcısı u, mesaj m, sonuç metni. Çıktı: Completed veya ret.

```
1. Transaction başlat; u kullanıcısını kilitle.
2. m mesajını ve hastasını bul; hasta, ardından mesaj satırını kilitle.
3. u aktif doctor/nurse, mesajın alıcısı ve hastaya atanmış mı?
   Koşullardan biri sağlanmıyorsa geri al.
4. Durum Pending değilse veya sonuç boş/1.000 karakterden uzunsa geri al.
5. Alıcı ve Pending koşulunu UPDATE işleminde de koru.
   status=Completed; result_text=sonuç; completed_at=kayıt zamanı.
6. Tam bir satır değiştiyse commit; aksi halde geri al.
```

> **Not:** Aynı görevi iki kez tamamlama isteğinde yalnız ilk geçerli durum değişimi kabul edilir. Hasta satırının kilitlenmesi küçük proje için basit bir tutarlılık tercihidir; aynı hastanın eşzamanlı yazmalarını sıraya koyar.
