> 🇬🇧 **English** · 🇹🇷 Türkçe sürüm aşağıdadır.

# 3.7–3.11 · Experimental Design — Experiment and evaluation plan

## 3.7 Experimental system

Functional evaluation is planned with one administrator, two doctors, one nurse and three synthetic patients. Deniz and Ece are assigned to P001, Bora to P002, and Deniz also to P003, which has no measurements. For the doctor-to-doctor message scenario, Bora is also assigned to P001. Each scenario is evaluated independently by returning to the initial data.

## 3.8 Measurement and data analysis

Correctness will be evaluated by comparing the expected patient/measurement/message IDs and status fields. For performance, 1,000, 10,000 and 100,000 measurements will be generated over a fixed set of 50 patients, and messages at the same scales for the task list. On the same data, Q2/Q3 will be compared without and with the selected secondary indexes; PK/UNIQUE indexes are kept. Each query will be run 5 times for warm-up and 30 times for measurement; median time, p95, blocks read and index size will be recorded. Hardware, version, data distribution and query parameters will be reported.

**Table 13. Verification scenarios of the project**

| Case | Expected result |
|---|---|
| Valid staff member opens an assigned patient | Only the related patient and permitted messages are shown. |
| Clinical access to an unassigned patient or by an administrator | No content is shown; no record changes. |
| The same patient–staff pair is assigned again | The second assignment is rejected. |
| Valid measurement / invalid type, value or time | The valid one is inserted once; the invalid one is not inserted. |
| Doctor sends to a nurse or another doctor on the same patient | One Pending record is created; result and completion time are empty. |
| A nurse sends; a doctor sends to themself or to unassigned staff | No message is created. |
| Recipient completes with a filled result | Completed; result and completion time are filled. |
| Another staff member, empty result or second completion | The current status and result are preserved. |
| Removing an assignment / deactivating while a pending task exists | The operation is rejected; the task remains accessible. |
| Deleting a patient/staff/type with dependent records | Record integrity is preserved; deletion is rejected. |
| Same query before and after indexing | The same result set and the specified order are obtained. |

## 3.9 Compound error testing

When an unassigned patient and an invalid measurement type are sent in the same request, no record must be created. When sending a task and removing the recipient’s assignment are attempted at the same time, depending on the order either the message must be rejected because the assignment was removed, or the assignment removal must be rejected because a pending task exists. No partial record may remain if an error occurs before commit.

## 3.10 Presentation of output results

The planned outputs are the patient list, the measurement history and the pending/completed task screens. Experiment evidence will be presented as screenshots with synthetic data, query plans and measurement tables. The acceptance criteria are that all defined functional scenarios give correct results, unauthorized data access is blocked, and results do not change in the index comparisons.

## 3.11 Discussion of the design

The six tables cover the persistent information of the scenario and the eight foreign key relationships. A single-recipient message with the result kept in the same row keeps the scope small. Manual measurement entry, a single department, and the absence of assignment history and record correction history are the limits of the design. The experiment method is defined here; no implementation test or performance measurement is reported as if it had already been done.

---

> 🇹🇷 **Türkçe**

# 3.7–3.11 · Experimental Design — Deney ve değerlendirme planı

## 3.7 Deney sistemi

İşlevsel değerlendirme bir yönetici, iki doktor, bir hemşire ve üç sentetik hastayla planlanmıştır. Deniz ve Ece P001’e, Bora P002’ye, Deniz ayrıca ölçümü olmayan P003’e atanır. Doktordan doktora mesaj senaryosunda Bora da P001’e atanır. Her senaryo başlangıç verisine dönülerek bağımsız değerlendirilir.

## 3.8 Ölçüm ve veri analizi

Doğruluk, beklenen hasta/ölçüm/mesaj numaraları ve durum alanları karşılaştırılarak değerlendirilecektir. Performans için sabit 50 hasta üzerinde 1.000, 10.000 ve 100.000 ölçüm; görev listesi için aynı ölçeklerde mesaj üretilecektir. Aynı veri üzerinde seçilen ikincil indeksler olmadan ve indekslerle Q2/Q3 karşılaştırılacak; PK/UNIQUE indeksleri korunacaktır. Her sorguda 5 ısınma, 30 ölçüm yapılacak; medyan süre, p95, okunan bloklar ve indeks boyutu kaydedilecektir. Donanım, sürüm, veri dağılımı ve sorgu parametreleri raporlanacaktır.

**Tablo 13. Projenin doğrulama senaryoları**

| Durum | Beklenen sonuç |
|---|---|
| Geçerli personel atanmış hastayı açar | Yalnız ilgili hasta ve izinli mesajlar görünür. |
| Atanmamış hasta veya yöneticiyle klinik erişim | İçerik gösterilmez; kayıt değişmez. |
| Aynı hasta–personel çifti tekrar atanır | İkinci atama reddedilir. |
| Geçerli ölçüm / geçersiz tür, değer veya zaman | Geçerli olan bir kez eklenir; hatalı olan eklenmez. |
| Doktor aynı hastadaki hemşireye veya başka doktora gönderir | Bir Pending kayıt oluşur; sonuç ve tamamlanma zamanı boştur. |
| Hemşire gönderir; doktor kendine/atanmamış personele gönderir | Mesaj oluşturulmaz. |
| Alıcı dolu sonuçla tamamlar | Completed; sonuç ve tamamlanma zamanı doludur. |
| Başka personel, boş sonuç veya ikinci tamamlama | Mevcut durum ve sonuç korunur. |
| Bekleyen alıcı görevi varken atama kaldırma/pasifleştirme | İşlem reddedilir; görev erişilebilir kalır. |
| Bağlı kaydı olan hasta/personel/tür silinir | Kayıt bütünlüğü korunur; silme reddedilir. |
| İndeks öncesi ve sonrası aynı sorgu | Aynı sonuç kümesi ve belirtilen sıra elde edilir. |

## 3.9 Birleşik hata deneyi

Atanmamış hasta ile geçersiz ölçüm türü aynı istekte gönderildiğinde hiçbir kayıt oluşmamalıdır. Görev gönderimi ile alıcının atamasını kaldırma aynı anda denendiğinde işlem sırasına göre ya atama kaldırıldığı için mesaj reddedilmeli ya da bekleyen görev oluştuğu için atama kaldırma reddedilmelidir. Commit öncesi hata durumunda yarım kayıt bırakılmamalıdır.

## 3.10 Çıktıların sunulması

Öngörülen çıktılar hasta listesi, ölçüm geçmişi ve bekleyen/tamamlanmış görev ekranlarıdır. Deney kanıtları sentetik verili ekran görüntüleri, sorgu planları ve ölçüm tabloları şeklinde sunulacaktır. Kabul ölçütleri tanımlı işlevsel senaryoların tamamının doğru sonuç vermesi, yetkisiz veri erişiminin engellenmesi ve indeks karşılaştırmalarında sonuçların değişmemesidir.

## 3.11 Tasarımın değerlendirilmesi

Altı tablo senaryodaki kalıcı bilgileri ve sekiz yabancı anahtar ilişkisini karşılamaktadır. Tek alıcılı mesaj ve aynı satırda sonuç tutma, kapsamı küçük tutar. Elle ölçüm girişi, tek bölüm, atama geçmişi ve kayıt düzeltme tarihçesinin bulunmaması tasarımın sınırlarıdır. Burada deney yöntemi tanımlanmıştır; uygulama testi veya performans ölçümü henüz yapılmış gibi sonuç verilmemektedir.
