> 🇬🇧 **English** · 🇹🇷 Türkçe sürüm aşağıdadır.

# Chapter 1 · Introduction — Project description and scenario

In a single department of a hospital, each patient's measurement history and the tasks given for that patient are tracked in one shared record structure.

## 1.1 Background

In patient monitoring studies, delivering information into the clinician's workflow is as important as collecting measurements. Electronic health record research identifies access control and data quality as common requirements. This project addresses these requirements in a small, department-level database design. [6] [11] [12] [16]

## 1.2 Project scenario

> The department administrator registers the patient and assigns the doctor and nurse who will care for the patient. Assigned staff record the patient's body temperature, pulse and blood pressure measurements with the date and time.
>
> The doctor opens the patient profile and reviews the measurements. When needed, the doctor sends a task message about the patient to a nurse or another doctor assigned to the same patient. After completing the task, the recipient writes a result note; the message moves from **Pending → Completed**. The link between the patient, the measurements and the tasks is preserved.

## 1.3 Expected benefit and 1.4 problem statement

Measurements kept in separate lists and tasks passed on verbally make it hard to track which record belongs to which patient and who completed a task. The proposed system links this information through the patient; the recorder, the task recipient and the result are clearly visible. This is an expected process benefit; no measured clinical success or cost saving is claimed. [7] [8] [17]

## 1.5 Objectives

- Store patient information and timestamped measurements consistently.
- Restrict doctor and nurse access to the patients they are assigned to.
- Send single-recipient tasks from a doctor to the relevant staff member and record the result.
- Meet these needs with six tables, explicit keys and verifiable business rules.

## 1.6 Scope and limitations

The system covers a single hospital department. Measurements are entered manually; there are no patient accounts, appointments, prescriptions, billing, sensor connections, automatic diagnosis or emergency alarms. Notifications are shown in the in-app task inbox. Record correction history and a multi-department structure are not part of this design.

## 1.7 Proposed solution and roles

**Table 1. User roles and project responsibilities**

| Role | Responsibility |
|---|---|
| Administrator · admin | Manages accounts, basic patient information and assignments. Has no access to clinical measurements or message contents. |
| Doctor · doctor | Reviews assigned patients and their measurements; adds measurements, sends tasks and completes tasks sent to them. |
| Nurse · nurse | Reviews assigned patients and their measurements; adds measurements and completes tasks sent to them. |

## 1.8 Development approach

The design was handled iteratively: the scenario and business rules were defined, entities were extracted, and the ER/UML models and relational schema were built. Any change in the rules must be reflected in the schema, queries and algorithms together.

## 1.9 Hardware and software selection

**1.9.1 Hardware:** A single personal computer is sufficient for development and the synthetic data experiment; no special medical device is used. The processor and memory of the computer used will be recorded in the experiment report.

**1.9.2 Software:** PostgreSQL was chosen for the database, Python/Flask for the server, HTML/CSS for the interface and draw.io for the diagrams. The browser communicates with the application server and never connects to the database directly. These are the technology choices of this design.

---

> 🇹🇷 **Türkçe**

# Chapter 1 · Introduction — Projenin tanımı ve senaryosu

Bir hastanenin tek bölümünde, hastanın ölçüm geçmişi ve o hasta için verilen görevler ortak bir kayıt düzeninde izlenir.

## 1.1 Arka plan

Hasta izleme çalışmalarında ölçümlerin toplanması kadar bilgilerin sağlık çalışanının iş akışına aktarılması da önemlidir. Elektronik sağlık kaydı araştırmaları ise erişim kontrolü ve veri kalitesini ortak gereksinimler olarak göstermektedir. Bu proje bu gereksinimleri küçük bir bölüm içi veritabanı tasarımında ele alır. [6] [11] [12] [16]

## 1.2 Proje senaryosu

> Bölüm yöneticisi hastayı sisteme kaydeder ve hastayla ilgilenecek doktor ile hemşireyi belirler. Atanmış personel hastanın vücut sıcaklığı, nabız ve kan basıncı ölçümlerini tarih ve saat bilgisiyle kaydeder.
>
> Doktor hasta profilini açarak ölçümleri inceler. Gerekli gördüğünde aynı hastaya atanmış hemşireye veya başka doktora hasta hakkında bir görev mesajı gönderir. Alıcı personel görevi yerine getirdikten sonra sonuç açıklamasını yazar; mesaj **Bekliyor → Tamamlandı** durumuna geçer. Hasta, ölçüm ve görev bilgileri arasındaki bağlantı korunur.

## 1.3 Beklenen fayda ve 1.4 problem tanımı

Ayrı listelerde tutulan ölçümler ve kişiye sözlü iletilen görevler, hangi kaydın hangi hastaya ait olduğunun ve görevin kim tarafından sonuçlandırıldığının takibini zorlaştırabilir. Önerilen sistem bu bilgileri hasta üzerinden ilişkilendirir; kaydeden kişi, görev alıcısı ve sonuç açıkça görülebilir. Bu, beklenen süreç faydasıdır; klinik başarı veya maliyet tasarrufu ölçüldüğü iddia edilmez. [7] [8] [17]

## 1.5 Amaçlar

- Hasta bilgilerini ve zaman damgalı ölçümleri tutarlı biçimde saklamak.
- Doktor ve hemşire erişimini görevli oldukları hastalarla sınırlandırmak.
- Doktordan ilgili personele tek alıcılı görev iletmek ve sonucunu kaydetmek.
- Bu ihtiyaçları altı tablo, açık anahtarlar ve denetlenebilir iş kurallarıyla karşılamak.

## 1.6 Kapsam ve sınırlar

Sistem tek bir hastane bölümünü kapsar. Ölçümler elle girilir; hasta hesabı, randevu, reçete, faturalama, sensör bağlantısı, otomatik teşhis ve acil alarm hizmeti bulunmaz. Bildirim, uygulamadaki görev kutusunda gösterilir. Kayıt düzeltme tarihçesi ve çok bölümlü yapı bu tasarıma dahil değildir.

## 1.7 Önerilen çözüm ve roller

**Tablo 1. Kullanıcı rolleri ve proje sorumlulukları**

| Rol | Sorumluluk |
|---|---|
| Yönetici · admin | Hesap, hasta temel bilgisi ve atama yönetimi. Klinik ölçüm ve mesaj içeriklerine erişmez. |
| Doktor · doctor | Atanmış hastaları ve ölçümlerini inceler; ölçüm ekler, görev gönderir ve kendisine gelen görevleri tamamlar. |
| Hemşire · nurse | Atanmış hastaları ve ölçümlerini inceler; ölçüm ekler ve kendisine gelen görevleri tamamlar. |

## 1.8 Geliştirme yaklaşımı

Tasarım yinelemeli olarak ele alınmıştır: senaryo ve iş kuralları belirlenmiş, varlıklar çıkarılmış, ER/UML modelleri ve ilişkisel şema oluşturulmuştur. Kurallardaki değişikliklerin şema, sorgu ve algoritmalara birlikte yansıtılması esastır.

## 1.9 Donanım ve yazılım seçimi

**1.9.1 Donanım:** Geliştirme ve sentetik veri deneyi için tek bir kişisel bilgisayar yeterlidir; özel tıbbi cihaz kullanılmaz. Deney raporunda kullanılan bilgisayarın işlemci ve bellek bilgisi kaydedilecektir.

**1.9.2 Yazılım:** Veritabanı için PostgreSQL, sunucu için Python/Flask, arayüz için HTML/CSS ve diyagramlar için draw.io seçilmiştir. Tarayıcı uygulama sunucusuyla iletişim kurar; veritabanına doğrudan bağlanmaz. Bunlar bu tasarımın teknoloji seçimleridir.
