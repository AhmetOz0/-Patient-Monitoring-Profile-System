# Patient Monitoring Profile System

**CME301 · Database Management Systems** — Course Project · Fall 2026

[English](#english) · [Türkçe](#türkçe) · [Team / Ekip](#team--ekip)

---

## English

### About the project

In this project we are developing an online patient monitoring database for a single department of a hospital. Doctors will be able to access their patients' records and health measurements through a web interface. When necessary, they will be able to send a message to a nurse or another doctor asking them to take an action. Since patient information is sensitive, the system must be secure and every user must see only the data they are authorized to see.

### How will it work?

1. The department administrator registers the patient and assigns the doctors and nurses responsible for that patient.
2. The assigned staff enter measurements such as body temperature, pulse and blood pressure, together with the date and time.
3. The doctor opens the patient's profile and reviews the measurement history.
4. If needed, the doctor sends a task message to a nurse or another doctor assigned to the same patient.
5. The recipient carries out the task, writes the result into the system, and the task is marked as completed.

### Users

| Role | What can they do? |
|---|---|
| Administrator | Manages staff accounts, patient records, and which staff member is responsible for which patient. |
| Doctor | Sees their own patients and measurements, adds measurements, sends task messages, completes tasks sent to them. |
| Nurse | Sees their own patients and measurements, adds measurements, completes tasks sent to them. |

### Goals

- Store patient information and health measurements in an organized and consistent way
- Ensure doctors and nurses can access only their own patients
- Allow doctors to assign tasks to the relevant staff and record the outcome
- Keep patient data secure

### Scope

**Included**
- Patient registration and patient–staff assignment
- Date- and time-stamped health measurements
- Task messages from doctors to staff, with task results
- Role-based access control

**Not included**
- Patient login
- Appointments, prescriptions and billing
- Device/sensor integration and automatic diagnosis
- Multiple departments or hospitals

### Database tables

The database consists of six tables.

| Table | Purpose | How it is used |
|---|---|---|
| `Users` | Staff accounts: username, full name, password hash, role (admin / doctor / nurse) and active status. | Login and role check on every request. Accounts are deactivated, not deleted. |
| `Patients` | Basic patient information: unique patient number, full name, birth date. | Created by the administrator; opened as the patient profile by assigned staff. |
| `PatientStaff` | Which doctor or nurse is currently assigned to which patient (many-to-many). | Every clinical access checks this table: staff see only their own patients. |
| `MeasurementTypes` | Measurement types and their units: body temperature (°C), pulse (bpm), systolic and diastolic blood pressure (mmHg). | Selected when a measurement is entered; the unit always comes from here. |
| `Measurements` | Each observation as a separate row: patient, type, value, observation time, record time, recorded by. | Assigned staff add measurements; the doctor reviews the history on the patient profile. |
| `Messages` | Task messages: patient, sender (doctor), recipient (doctor/nurse), text, status (Pending / Completed), result. | The doctor sends a task; the recipient completes it by writing the result. |

### Technologies

| Area | Tool |
|---|---|
| Database | PostgreSQL |
| Server | Python / Flask |
| Interface | HTML / CSS |
| Diagrams | draw.io |
| Version control | Git / GitHub |

### Roadmap

#### Phase 1 — Design and report (60%)
Deadline: last Friday of week 7 · Presentation: week 9

- [x] Introduction (project description, problem, goals, scope, method, hardware/software)
- [x] Literature review (at least 20 papers from 2014 onwards)
- [x] Research methodology
- [x] Entity modeling and business rules
- [x] ER and UML diagrams, table design
- [x] Relational algebra
- [x] Indexing structures
- [x] Algorithms for relational databases
- [x] Experiment and evaluation plan

#### Phase 2 — Implementation (40%)
Deadline: last Friday of week 12 · Demo: week 13

- [ ] SQL statements (tables, constraints, queries)
- [ ] Security levels
- [ ] GUI application
- [ ] Testing: how the system responds to invalid selections

### Folder structure

```
phase1/   Phase 1 report and diagrams
phase2/   SQL, application code and tests
docs/     Task allocation and contribution records
```

---

## Türkçe

### Proje hakkında

Bu projede bir hastanenin tek bir bölümü için çevrim içi bir hasta izleme veritabanı geliştiriyoruz. Doktorlar web arayüzünden kendi hastalarının kayıtlarına ve sağlık ölçümlerine ulaşabilecek. Gerekli gördüklerinde bir hemşireye veya başka bir doktora mesaj göndererek ondan bir iş yapmasını isteyebilecek. Hasta bilgileri hassas olduğu için sistemin güvenli olması ve herkesin yalnızca yetkili olduğu verileri görmesi önemlidir.

### Nasıl çalışacak?

1. Bölüm yöneticisi hastayı sisteme kaydeder ve hastayla ilgilenecek doktor ile hemşireleri belirler.
2. Hastayla ilgilenen personel vücut sıcaklığı, nabız ve kan basıncı gibi ölçümleri tarih ve saatiyle sisteme girer.
3. Doktor hastanın profilini açarak geçmiş ölçümleri inceler.
4. Doktor gerekli görürse aynı hastayla ilgilenen bir hemşireye veya başka bir doktora görev mesajı gönderir.
5. Mesajı alan kişi görevi yerine getirir, sonucu sisteme yazar ve görev tamamlanmış olarak işaretlenir.

### Kullanıcılar

| Rol | Ne yapabilir? |
|---|---|
| Yönetici | Personel hesaplarını, hasta kayıtlarını ve hangi personelin hangi hastayla ilgileneceğini yönetir. |
| Doktor | Kendi hastalarını ve ölçümlerini görür, ölçüm ekler, görev mesajı gönderir, kendisine gelen görevleri tamamlar. |
| Hemşire | Kendi hastalarını ve ölçümlerini görür, ölçüm ekler, kendisine gelen görevleri tamamlar. |

### Hedefler

- Hasta bilgilerini ve sağlık ölçümlerini düzenli ve tutarlı biçimde saklamak
- Doktor ve hemşirelerin yalnızca kendi hastalarına erişebilmesini sağlamak
- Doktorun ilgili personele görev iletebilmesi ve görevin sonucunun kaydedilmesi
- Hasta verilerini güvenli tutmak

### Kapsam

**Projeye dahil olanlar**
- Hasta kaydı ve hasta–personel eşleştirmesi
- Tarih ve saatli sağlık ölçümleri
- Doktordan personele görev mesajı ve görev sonucu
- Rol tabanlı erişim kontrolü

**Projeye dahil olmayanlar**
- Hastaların sisteme giriş yapması
- Randevu, reçete ve faturalama
- Cihaz/sensör bağlantısı ve otomatik teşhis
- Birden fazla bölüm veya hastane

### Veritabanı tabloları

Veritabanı altı tablodan oluşur.

| Tablo | Görevi | Nasıl kullanılır? |
|---|---|---|
| `Users` | Personel hesapları: kullanıcı adı, ad soyad, parola özeti, rol (yönetici / doktor / hemşire) ve aktiflik bilgisi. | Girişte ve her istekte rol kontrolü için kullanılır. Hesaplar silinmez, pasifleştirilir. |
| `Patients` | Hastanın temel bilgileri: benzersiz hasta numarası, ad soyad, doğum tarihi. | Yönetici tarafından kaydedilir; atanmış personel hasta profili olarak açar. |
| `PatientStaff` | Hangi doktor veya hemşirenin hangi hastaya atandığı (çoktan çoğa ilişki). | Her klinik erişimde kontrol edilir: personel yalnızca kendi hastalarını görür. |
| `MeasurementTypes` | Ölçüm türleri ve birimleri: vücut sıcaklığı (°C), nabız (bpm), sistolik ve diyastolik kan basıncı (mmHg). | Ölçüm girilirken seçilir; birim her zaman buradan alınır. |
| `Measurements` | Her ölçüm ayrı bir satır: hasta, tür, değer, ölçüm zamanı, kayıt zamanı, kaydeden kişi. | Atanmış personel ölçüm ekler; doktor geçmişi hasta profilinde inceler. |
| `Messages` | Görev mesajları: hasta, gönderen (doktor), alıcı (doktor/hemşire), metin, durum (Bekliyor / Tamamlandı), sonuç. | Doktor görev gönderir; alıcı sonucu yazarak görevi tamamlar. |

### Kullanılacak teknolojiler

| Alan | Araç |
|---|---|
| Veritabanı | PostgreSQL |
| Sunucu | Python / Flask |
| Arayüz | HTML / CSS |
| Diyagramlar | draw.io |
| Sürüm kontrolü | Git / GitHub |

### Yol haritası

#### Phase 1 — Tasarım ve rapor (%60)
Teslim: 7. haftanın son Cuması · Sunum: 9. hafta

- [x] Giriş (proje tanımı, problem, hedefler, kapsam, yöntem, donanım/yazılım)
- [x] Literatür taraması (2014 sonrası en az 20 yayın)
- [x] Araştırma yöntemi
- [x] Varlık modelleme ve iş kuralları
- [x] ER ve UML diyagramları, tablo tasarımı
- [x] İlişkisel cebir
- [x] İndeks yapıları
- [x] İlişkisel veritabanı algoritmaları
- [x] Deney ve değerlendirme planı

#### Phase 2 — Uygulama (%40)
Teslim: 12. haftanın son Cuması · Demo: 13. hafta

- [ ] SQL ifadeleri (tablolar, kısıtlar, sorgular)
- [ ] Güvenlik seviyeleri
- [ ] Arayüz (GUI) uygulaması
- [ ] Test: hatalı seçimlerde sistemin verdiği tepkiler

### Klasör yapısı

```
phase1/   Phase 1 raporu ve diyagramlar
phase2/   SQL, uygulama kodu ve testler
docs/     Görev dağılımı ve katkı kayıtları
```

---

## Team / Ekip

| Name / Ad Soyad | Responsibility / Sorumluluk |
|---|---|
| Talha Kılınçaslan | Team leader, methodology, evaluation plan / Grup lideri, yöntem, deney planı |
| Ahmed Emin Özaslan | Introduction, README, report compilation / Giriş, README, raporun derlenmesi |
| Aslı Polat | Business rules K01–K15, draw.io ER guide / İş kuralları K01–K15, draw.io ER rehberi |
| Zeynep Şule Akın | Business rules K16–K24, literature 1–10 / İş kuralları K16–K24, literatür 1–10 |
| İbrahim Çakır | ER diagram, abstract / ER diyagramı, özet |
| Muhammed Güzel | UML diagram, literature 11–20, references / UML diyagramı, literatür 11–20, kaynakça |
| Osman Salih Akbulut | Table design (core), tables overview / Tablo tasarımı (çekirdek), tablo özeti |
| Muhammed Emir Köroğlu | Table design (clinical), 3NF, indexing / Tablo tasarımı (klinik), 3NF, indeksler |
| Aslı Didem Aslan | Relational algebra, algorithms / İlişkisel cebir, algoritmalar |

**Working rule:** Every member commits and pushes their own part from their own GitHub account, with a commit message that clearly states the work done (e.g. `Literature: first 10 papers added`). Each member prepares a short contribution record with the Phase 1 submission.

**Çalışma kuralı:** Her üye kendi bölümünü kendi GitHub hesabından commit ve push eder. Commit mesajı yapılan işi açıkça söylemelidir (örn. `Literatür: ilk 10 yayın eklendi`). Her üye Phase 1 teslimiyle birlikte kısa bir katkı kaydı hazırlar.
