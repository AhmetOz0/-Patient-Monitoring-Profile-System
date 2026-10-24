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

- [ ] Introduction (project description, problem, goals, scope, method, hardware/software)
- [ ] Literature review (at least 20 papers from 2014 onwards)
- [ ] Research methodology
- [ ] Entity modeling and business rules
- [ ] ER and UML diagrams, table design
- [ ] Relational algebra
- [ ] Indexing structures
- [ ] Algorithms for relational databases
- [ ] Experiment and evaluation plan

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

- [ ] Giriş (proje tanımı, problem, hedefler, kapsam, yöntem, donanım/yazılım)
- [ ] Literatür taraması (2014 sonrası en az 20 yayın)
- [ ] Araştırma yöntemi
- [ ] Varlık modelleme ve iş kuralları
- [ ] ER ve UML diyagramları, tablo tasarımı
- [ ] İlişkisel cebir
- [ ] İndeks yapıları
- [ ] İlişkisel veritabanı algoritmaları
- [ ] Deney ve değerlendirme planı

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

| Name / Ad Soyad | GitHub | Responsibility / Sorumluluk |
|---|---|---|
| | | Team leader, coordination / Grup lideri, koordinasyon |
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |

**Working rule:** Every member commits and pushes their own part from their own GitHub account, with a commit message that clearly states the work done (e.g. `Literature: first 10 papers added`). Each member prepares a short contribution record with the Phase 1 submission.

**Çalışma kuralı:** Her üye kendi bölümünü kendi GitHub hesabından commit ve push eder. Commit mesajı yapılan işi açıkça söylemelidir (örn. `Literatür: ilk 10 yayın eklendi`). Her üye Phase 1 teslimiyle birlikte kısa bir katkı kaydı hazırlar.
