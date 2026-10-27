> 🇬🇧 **English** · 🇹🇷 Türkçe sürüm aşağıdadır.

# 3.6.4 · Relational Algebra — Relational algebra expressions of the project

The expressions below define the data needs of the project screens directly. `u` is the staff member in the session and `p` is the selected patient. Before clinical queries an active doctor/nurse account is verified; for Q2 and Q5 the current assignment to the patient is also verified.

## Q1 · Staff member’s patients

IDs and names of the patients assigned to staff member u.

```
Aᵤ = σ user_id=u (PatientStaff)
π Patients.patient_id, patient_no, full_name
  (Patients ⋈ Patients.patient_id=Aᵤ.patient_id Aᵤ)
```

The staff member’s assignments are selected first and then joined with patient information.

> **Synthetic example:** For Doctor Deniz, u=2. Assignment pairs (patient_id, user_id) = (1, 2) and (3, 2).
> **Expected output:** 1 · P001 · Demo Patient A — 3 · P003 · Demo Patient C

## Q2 · Measurement history

Measurements of patient p in the interval [t₀, t₁) with their units.

```
Mₚ = σ patient_id=p ∧ t₀≤observed_at ∧ observed_at<t₁ (Measurements)
π measurement_id, name, value, unit, observed_at
  (Mₚ ⋈ Mₚ.type_id=MeasurementTypes.type_id MeasurementTypes)
```

The patient and time interval are filtered; the type name and unit come from the catalogue. The algebra result is unordered; on screen it is shown in descending order of observation time and measurement ID.

> **Synthetic example:** p=1 (patient record no P001); sample day 18 October 2026.
> **Expected output:** Measurement 2 · 09:05 · Pulse · 80 bpm — Measurement 1 · 09:00 · Body temperature · 36.70 °C

## Q3 · Pending tasks

Pending messages of recipient u for patients u is currently assigned to.

```
Aᵤ = π patient_id (σ user_id=u (PatientStaff))
Gᵤ = σ recipient_id=u ∧ status='Pending' (Messages)
π message_id, Gᵤ.patient_id, body, created_at
  (Gᵤ ⋈ Gᵤ.patient_id=Aᵤ.patient_id Aᵤ)
```

The recipient and status filter is applied; matching with patient assignments preserves the access boundary.

> **Synthetic example:** For Nurse Ece, u=3; she is assigned to patient 1 (P001) and this patient has one Pending message.
> **Expected output:** Message 1 · Patient 1 (P001) · 18 October 2026, 09:10 — Please record a follow-up measurement. · Pending

## Q4 · Patients without measurements

IDs of patients assigned to the staff member who have no measurements yet.

```
Aᵤ = π patient_id (σ user_id=u (PatientStaff))
Ö = π patient_id (Measurements)
Aᵤ − Ö
```

Patient IDs that have measurements are subtracted from the set of assigned patient IDs. Both sides have the same single-column schema.

> **Synthetic example:** Deniz: patient 1 (P001) and patient 3 (P003). Only patient 1 has measurements.
> **Expected output:** patient_id = 3 · Patient record no P003

## Q5 · Authorized messages for a patient

Messages for patient p that user u sent or received.

```
S = σ patient_id=p ∧ sender_id=u (Messages)
R = σ patient_id=p ∧ recipient_id=u (Messages)
S ∪ R
```

Both results are Messages rows with the same schema. The union satisfies the sender/recipient condition. User u’s current assignment to patient p is checked first.

> **Synthetic example:** Deniz u=2, patient p=1 (P001). Deniz is the sender of message 1.
> **Expected output:** Message 1 · Patient 1 · Deniz → Ece · Pending

---

**Notation:** σ selection, π projection, ⋈ conditional join, − set difference, ∪ union. If Users is joined in two different roles, it is renamed as ρ_Sender(Users) and ρ_Recipient(Users). Example results are illustrative; they are not experiment outputs from a running database.

---

> 🇹🇷 **Türkçe**

# 3.6.4 · Relational Algebra — Projenin ilişkisel cebir ifadeleri

Aşağıdaki ifadeler doğrudan proje ekranlarının veri ihtiyacını tanımlar. `u` oturumdaki personel, `p` seçilen hastadır. Klinik sorgulardan önce aktif doctor/nurse hesabı; Q2 ve Q5 için ayrıca ilgili hastanın güncel ataması doğrulanır.

## Q1 · Personelin hastaları

u numaralı personele atanmış hastaların numara ve adları.

```
Aᵤ = σ user_id=u (PatientStaff)
π Patients.patient_id, patient_no, full_name
  (Patients ⋈ Patients.patient_id=Aᵤ.patient_id Aᵤ)
```

Önce ilgili personelin atamaları seçilir; ardından hasta bilgileriyle birleştirilir.

> **Sentetik örnek:** Doktor Deniz için u=2. Atama çiftleri (patient_id, user_id) = (1, 2) ve (3, 2).
> **Beklenen çıktının özeti:** 1 · P001 · Demo Hasta A — 3 · P003 · Demo Hasta C

## Q2 · Ölçüm geçmişi

p hastasının [t₀, t₁) aralığındaki ölçümleri ve birimleri.

```
Mₚ = σ patient_id=p ∧ t₀≤observed_at ∧ observed_at<t₁ (Measurements)
π measurement_id, name, value, unit, observed_at
  (Mₚ ⋈ Mₚ.type_id=MeasurementTypes.type_id MeasurementTypes)
```

Hasta ve zaman aralığı filtrelenir; tür adı ile birimi katalogdan alınır. Cebir sonucu sırasızdır; ekranda gözlem zamanı ve ölçüm kimliği azalan sırada gösterilir.

> **Sentetik örnek:** p=1 (hasta kayıt no P001); örnek gün 18 Ekim 2026.
> **Beklenen çıktının özeti:** Ölçüm 2 · 09:05 · Nabız · 80 bpm — Ölçüm 1 · 09:00 · Vücut sıcaklığı · 36,70 °C

## Q3 · Bekleyen görevler

u alıcısının, hâlen atandığı hastalara ait bekleyen mesajları.

```
Aᵤ = π patient_id (σ user_id=u (PatientStaff))
Gᵤ = σ recipient_id=u ∧ status='Pending' (Messages)
π message_id, Gᵤ.patient_id, body, created_at
  (Gᵤ ⋈ Gᵤ.patient_id=Aᵤ.patient_id Aᵤ)
```

Alıcı ve durum filtresi uygulanır; hasta atamasıyla eşleştirme erişim sınırını korur.

> **Sentetik örnek:** Hemşire Ece için u=3; hasta 1 (P001) ataması ve bu hastada bir Pending mesajı vardır.
> **Beklenen çıktının özeti:** Mesaj 1 · Hasta 1 (P001) · 18 Ekim 2026, 09:10 — Kontrol ölçümünü kaydediniz. · Bekliyor

## Q4 · Ölçümü olmayan hastalar

Personele atanmış fakat henüz hiç ölçümü kaydedilmemiş hastaların numaraları.

```
Aᵤ = π patient_id (σ user_id=u (PatientStaff))
Ö = π patient_id (Measurements)
Aᵤ − Ö
```

Atanmış hasta numaraları kümesinden ölçümü bulunan hasta numaraları çıkarılır. İki taraf da aynı tek sütunlu şemaya sahiptir.

> **Sentetik örnek:** Deniz: hasta 1 (P001) ve hasta 3 (P003). Yalnız hasta 1’in ölçümü vardır.
> **Beklenen çıktının özeti:** patient_id = 3 · Hasta kayıt no P003

## Q5 · Hastanın yetkili mesajları

p hastasında u kullanıcısının gönderdiği veya aldığı mesajlar.

```
S = σ patient_id=p ∧ sender_id=u (Messages)
R = σ patient_id=p ∧ recipient_id=u (Messages)
S ∪ R
```

İki sonuç aynı şemalı Messages satırlarıdır. Birleşim gönderen/alıcı koşulunu karşılar. Önce u kullanıcısının p hastasına güncel ataması kontrol edilir.

> **Sentetik örnek:** Deniz u=2, hasta p=1 (P001). Deniz 1 numaralı mesajın göndericisidir.
> **Beklenen çıktının özeti:** Mesaj 1 · Hasta 1 · Deniz → Ece · Bekliyor

---

**Gösterim:** σ seçim, π sütun seçimi, ⋈ koşullu birleştirme, − küme farkı, ∪ birleşim. Users iki farklı rolle birleştirilecekse ρ_Gönderen(Users) ve ρ_Alıcı(Users) olarak yeniden adlandırılır. Örnek sonuçlar açıklama amaçlıdır; çalışan veritabanından alınmış deney çıktıları değildir.
