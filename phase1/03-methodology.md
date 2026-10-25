> 🇬🇧 **English** · 🇹🇷 Türkçe sürüm aşağıdadır.

# Chapter 3 · Research Methodology — Method and design approach

## 3.1 Method

The patient, staff, assignment, measurement type, measurement and task message information in the scenario was modelled as separate responsibilities. Business rules were first written in natural language and then mapped to keys, multiplicities, constraints and transaction steps.

## 3.2 Need addressed

The need addressed in this project is tracking a patient's measurement history together with the tasks given to staff, at the scale of a single department. It is not claimed that this need is unsolved in the literature; the contribution of the work is turning the selected narrow scope into a consistent relational design. [10] [15] [16]

## 3.3 Existing approaches and 3.4 comparison

**Table 2. Design alternatives considered in the project**

| Decision | Alternative | Chosen approach and reason |
|---|---|---|
| Patient–staff link | A single doctor field inside Patients | PatientStaff: allows more than one doctor/nurse to be assigned to the same patient. |
| Storing measurements | A separate column per type in the patient table | Measurements + MeasurementTypes: stores repeated observations as dated rows with a shared unit. |
| Task result | Separate tables for message, reply and notification | Status and a single result inside Messages: sufficient for this project's single-recipient task. |
| Access | Role check only | Role + current patient assignment; plus a sender/recipient check for messages. |

## 3.5 Project-specific transaction algorithm

The doctor's patient selection, measurement review, recipient selection and task delivery are defined as one flow that ends with the recipient recording the result. The checks and state change are given in the transaction algorithms. This is transaction logic prepared for the project; it is not a new database engine algorithm or a scientific novelty claim.

## 3.6 Proposed system design

The business rules, six tables, ER/UML diagrams, algebra expressions and index plan are parts of the same design. The **patient profile** is a screen that combines Patients with the related measurements and authorized messages; it is not a seventh table.

---

> 🇹🇷 **Türkçe**

# Chapter 3 · Research Methodology — Yöntem ve tasarım yaklaşımı

## 3.1 Yöntem

Senaryodaki hasta, personel, atama, ölçüm türü, ölçüm ve görev mesajı bilgileri ayrı sorumluluklar olarak modellenmiştir. İş kuralları önce doğal dille yazılmış, sonra anahtarlar, çokluklar, kısıtlar ve işlem adımlarıyla eşleştirilmiştir.

## 3.2 Ele alınan ihtiyaç

Bu projede çözülen ihtiyaç, tek bölüm ölçeğinde hastanın ölçüm geçmişi ile personele verilen görevin birlikte izlenmesidir. Literatürde bu ihtiyacın hiç çözülmediği ileri sürülmez; çalışmanın katkısı, seçilen dar kapsamın tutarlı bir ilişkisel tasarıma dönüştürülmesidir. [10] [15] [16]

## 3.3 Mevcut yaklaşımlar ve 3.4 karşılaştırma

**Tablo 2. Proje kapsamında değerlendirilen tasarım seçenekleri**

| Karar | Alternatif | Seçilen yaklaşım ve nedeni |
|---|---|---|
| Hasta–personel bağlantısı | Patients içinde tek doktor alanı | PatientStaff: aynı hastaya birden fazla doktor/hemşire atanabilmesini sağlar. |
| Ölçüm saklama | Her tür için hasta tablosunda ayrı sütun | Measurements + MeasurementTypes: tekrar eden gözlemleri tarihli satırlarda, ortak birimle saklar. |
| Görev sonucu | Mesaj, yanıt ve bildirim için ayrı tablolar | Messages içinde durum ve tek sonuç: bu projenin tek alıcılı görevi için yeterlidir. |
| Erişim | Yalnızca rol kontrolü | Rol + güncel hasta ataması; mesajda ayrıca gönderen/alıcı kontrolü. |

## 3.5 Projeye özgü işlem algoritması

Doktorun hasta seçimi, ölçüm incelemesi, alıcı seçimi ve görev iletimi; alıcının sonuç kaydıyla tamamlanan bir akış olarak tanımlanmıştır. Kontroller ve durum değişimi işlem algoritmalarında verilmiştir. Bu, proje için hazırlanmış işlem mantığıdır; yeni bir veritabanı motoru algoritması veya bilimsel yenilik iddiası değildir.

## 3.6 Önerilen sistem tasarımı

İş kuralları, altı tablo, ER/UML diyagramları, cebir ifadeleri ve indeks planı aynı tasarımın parçalarıdır. **Hasta profili**, Patients ile ilgili ölçüm ve yetkili mesajların birleştirildiği ekrandır; yedinci bir tablo değildir.
