> 🇬🇧 **English** · 🇹🇷 Türkçe sürüm aşağıdadır.

# Chapter 2 · Literature Review (11–20) — Data security, communication and experimental studies

This file contains the second half of the 20 reviewed papers and the design implications drawn from the literature.

### [11] · 2017 · Data and security
**Personal Health Records: A Systematic Literature Review**
Roehrs A, da Costa CA, Righi RDR, de Oliveira KSF · Journal of Medical Internet Research, 19(1), e13

- **Method:** Classification of data, architecture, user profiles and open issues in personal health records.
- **Finding:** Privacy, access control, usability and interoperability are common challenges.
- **Limitation:** It covers PHR systems accessed by patients; this project has no patient accounts.
- **Relevance to the project:** Patient data and staff identity are separated; Patients, Users and PatientStaff carry separate responsibilities.
- DOI: [10.2196/jmir.5876](https://doi.org/10.2196/jmir.5876)

### [12] · 2017 · Data and security
**Patient Health Record Systems Scope and Functionalities: Literature Review and Future Directions**
Bouayad L, Ialynytchev A, Padmanabhan B · Journal of Medical Internet Research, 19(11), e388

- **Method:** Detailed review of 106 publications on personal health record data types and functions.
- **Finding:** New data types including time series and functions from access to analytics are classified; the need for data quality is emphasised.
- **Limitation:** Patient-oriented systems, mostly in the US context, were reviewed.
- **Relevance to the project:** Each measurement is a separate dated row; type and unit are standardised. Prediction and recommendation features are out of scope.
- DOI: [10.2196/jmir.8073](https://doi.org/10.2196/jmir.8073)

### [13] · 2017 · Data and security
**Security Techniques for the Electronic Health Records**
Kruse CS, Smith B, Vanderlinden H, Nealand A · Journal of Medical Systems, 41, 127

- **Method:** Review of publications on electronic health record security under administrative, physical and technical safeguards.
- **Finding:** Security is a multi-layered topic that cannot be reduced to a single encryption feature.
- **Limitation:** The review does not provide a security test or legal compliance certificate for a specific application.
- **Relevance to the project:** Password hashing, server authorisation, HTTPS, a restricted DB account and backups are planned together.
- DOI: [10.1007/s10916-017-0778-4](https://doi.org/10.1007/s10916-017-0778-4)

### [14] · 2015 · Data and security
**A systematic literature review on security and privacy of electronic health record systems: technical perspectives**
Rezaeibagha F, Win KT, Susilo W · Health Information Management Journal, 44(3), 23–38

- **Method:** Evaluation of 55 publications for technical security and privacy features.
- **Finding:** Access policies, data sharing, architecture and cryptography are among the features that must be handled together.
- **Limitation:** The primary studies are from 1998–2013; the paper was published in 2015, so it meets the assignment’s date requirement.
- **Relevance to the project:** The user’s role and patient assignment are checked separately; the access decision is made again on every server request.
- DOI: [10.1177/183335831504400304](https://doi.org/10.1177/183335831504400304)

### [15] · 2020 · Communication
**Health Care Professionals’ Experiences of Patient-Professional Communication Over Patient Portals: Systematic Review of Qualitative Studies**
Laukka E, Huhtakangas M, Heponiemi T, et al. · Journal of Medical Internet Research, 22(12), e21623

- **Method:** Thematic synthesis of 13 qualitative studies on health professionals’ online communication experiences.
- **Finding:** Alongside access and communication benefits, extra workload, misinterpretation and insufficient training were reported.
- **Limitation:** It studies patient–professional communication; it is not direct evidence of effectiveness for this project’s staff-to-staff flow.
- **Relevance to the project:** A single recipient, an explicit message status and a mandatory result note are used; no emergency notification service is promised.
- DOI: [10.2196/21623](https://doi.org/10.2196/21623)

### [16] · 2025 · Communication
**Networked Behaviors Associated With a Large-Scale Secure Messaging Network: Cross-Sectional Secondary Data Analysis**
Baratta LR, Xia L, Lew D, et al. · JMIR Medical Informatics, 13, e66544

- **Method:** Social network and clustering analysis of six months of EHR messaging data in one health system.
- **Finding:** Messaging connections and behaviours differed by staff role and work setting.
- **Limitation:** One health system and one messaging platform were studied; observational associations do not show causation.
- **Relevance to the project:** Patient, sender and recipient are separate FK fields in messages; the person responsible for a task is explicit.
- DOI: [10.2196/66544](https://doi.org/10.2196/66544)

### [17] · 2025 · Monitoring
**Clinical benefits and risks of remote patient monitoring: an overview and assessment of methodological rigour of systematic reviews for selected patient groups**
Wartenberg C, Elden H, Frerichs M, et al. · BMC Health Services Research, 25, 133

- **Method:** Methodological assessment of 84 systematic reviews on 16 patient groups using QUICKSTAR.
- **Finding:** Only a part reached adequate methodological quality; for many groups the evidence to assess benefits and risks is limited.
- **Limitation:** Results are limited to the selected groups and the quality of the reviews.
- **Relevance to the project:** No benefit percentage is written before experiment results exist; technical and clinical validation are kept separate.
- DOI: [10.1186/s12913-025-12292-w](https://doi.org/10.1186/s12913-025-12292-w)

### [18] · 2016 · Experimental study
**Effectiveness of Remote Patient Monitoring After Discharge of Hospitalized Patients With Heart Failure: The Better Effectiveness After Transition–Heart Failure (BEAT-HF) Randomized Clinical Trial**
Ong MK, Romano PS, Edgington S, et al. · JAMA Internal Medicine, 176(3), 310–318

- **Method:** Randomised trial with 1,437 participants comparing telephone support and telemonitoring with usual care.
- **Finding:** No significant reduction in 180-day all-cause readmission was shown.
- **Limitation:** A specific patient population and care transition intervention; it does not directly measure the success of a database design.
- **Relevance to the project:** The evaluation uses a baseline comparison and predefined acceptance criteria.
- DOI: [10.1001/jamainternmed.2015.7712](https://doi.org/10.1001/jamainternmed.2015.7712)

### [19] · 2018 · Experimental study
**Efficacy of telemedical interventional management in patients with heart failure (TIM-HF2): a randomised, controlled, parallel-group, unmasked trial**
Koehler F, Koehler K, Deckwart O, et al. · The Lancet, 392(10152), 1047–1057

- **Method:** Randomised trial of 1,571 patients comparing structured remote management with usual care.
- **Finding:** In the defined patient group, a reduction was reported in the percentage of days lost to unplanned cardiovascular admission and all-cause death.
- **Limitation:** The result belongs to the whole of technology, team and care process; it cannot be transferred to this small prototype.
- **Relevance to the project:** The flow measurement → doctor review → task to responsible staff → result is modelled explicitly.
- DOI: [10.1016/S0140-6736(18)31880-4](https://doi.org/10.1016/S0140-6736(18)31880-4)

### [20] · 2026 · Usability
**Digital Health Interventions to Support Chronic Disease Management: Systematic Scoping Review**
Al Mahmud A, Joachim S, Jayaraman PP, et al. · JMIR mHealth and uHealth, 14, e63742

- **Method:** Scoping review of the design, development and evaluation features of 69 digital platforms.
- **Finding:** Short-term results are mostly reported as positive, while long-term use, technical problems and engagement are important limits.
- **Limitation:** Many studies are short-term pilots; patient self-management is broader than the scope of this assignment.
- **Relevance to the project:** A design with few screens and task-based user trials is preferred; no long-term benefit is claimed.
- DOI: [10.2196/63742](https://doi.org/10.2196/63742)

## Design implications from the literature

The results of monitoring studies vary with the technology, patient group and care process. For this reason the project’s success will be evaluated through correct records, controlled access and a traceable task result, not on the assumption that it improves health outcomes. The measurement type/unit separation supports data quality, the patient–staff assignment supports the access boundary, and the single-recipient message supports task responsibility. [4] [10] [12] [14] [16] [19]

---

> 🇹🇷 **Türkçe**

# Chapter 2 · Literature Review (11–20) — Veri güvenliği, iletişim ve deneysel çalışmalar

Bu dosya incelenen 20 yayının ikinci yarısını ve literatürden çıkan tasarım kararlarını içerir.

### [11] · 2017 · Veri ve güvenlik
**Personal Health Records: A Systematic Literature Review**
Roehrs A, da Costa CA, Righi RDR, de Oliveira KSF · Journal of Medical Internet Research, 19(1), e13

- **Yöntem:** Kişisel sağlık kayıtlarında veri, mimari, kullanıcı profilleri ve açık sorunların sınıflandırılması.
- **Bulgu:** Gizlilik, erişim kontrolü, kullanılabilirlik ve sistemler arası uyum ortak güçlüklerdir.
- **Sınırlılık:** Hasta tarafından erişilen PHR sistemlerini ele alır; bu projede hasta hesabı bulunmaz.
- **Projedeki karşılığı:** Hasta verisi ile personel kimliği ayrılır; Patients, Users ve PatientStaff ayrı sorumluluk taşır.
- DOI: [10.2196/jmir.5876](https://doi.org/10.2196/jmir.5876)

### [12] · 2017 · Veri ve güvenlik
**Patient Health Record Systems Scope and Functionalities: Literature Review and Future Directions**
Bouayad L, Ialynytchev A, Padmanabhan B · Journal of Medical Internet Research, 19(11), e388

- **Yöntem:** 106 yayının kişisel sağlık kaydı veri türleri ve işlevleri açısından ayrıntılı incelenmesi.
- **Bulgu:** Zaman serileri dahil yeni veri türleri ve erişimden analitiğe uzanan işlevler sınıflandırılmıştır; veri kalitesi gereksinimi vurgulanır.
- **Sınırlılık:** Hasta odaklı ve ağırlıkla ABD bağlamındaki sistemler incelenmiştir.
- **Projedeki karşılığı:** Her ölçüm ayrı tarihli satırdır; tür ve birim standardize edilir. Tahmin ve öneri özellikleri kapsam dışıdır.
- DOI: [10.2196/jmir.8073](https://doi.org/10.2196/jmir.8073)

### [13] · 2017 · Veri ve güvenlik
**Security Techniques for the Electronic Health Records**
Kruse CS, Smith B, Vanderlinden H, Nealand A · Journal of Medical Systems, 41, 127

- **Yöntem:** Elektronik sağlık kaydı güvenliğine ilişkin yayınların idari, fiziksel ve teknik önlemler altında incelenmesi.
- **Bulgu:** Güvenlik, yalnızca bir şifreleme özelliğine indirgenemeyen çok katmanlı bir konudur.
- **Sınırlılık:** Derleme, belirli bir uygulamanın güvenlik testini veya yasal uygunluk belgesini sağlamaz.
- **Projedeki karşılığı:** Parola özeti, sunucu yetkilendirmesi, HTTPS, sınırlı DB hesabı ve yedekleme birlikte planlanır.
- DOI: [10.1007/s10916-017-0778-4](https://doi.org/10.1007/s10916-017-0778-4)

### [14] · 2015 · Veri ve güvenlik
**A systematic literature review on security and privacy of electronic health record systems: technical perspectives**
Rezaeibagha F, Win KT, Susilo W · Health Information Management Journal, 44(3), 23–38

- **Yöntem:** 55 yayının güvenlik ve mahremiyet teknik özellikleri açısından değerlendirilmesi.
- **Bulgu:** Erişim politikaları, veri paylaşımı, mimari ve kriptografi birlikte ele alınması gereken özellikler arasındadır.
- **Sınırlılık:** İncelenen birincil çalışmalar 1998–2013 dönemindendir; yayın tarihi 2015 olduğu için ödevin tarih koşuluna uygundur.
- **Projedeki karşılığı:** Kullanıcının rolü ile hasta ataması ayrı kontrol edilir; erişim kararı her sunucu isteğinde yeniden verilir.
- DOI: [10.1177/183335831504400304](https://doi.org/10.1177/183335831504400304)

### [15] · 2020 · İletişim
**Health Care Professionals’ Experiences of Patient-Professional Communication Over Patient Portals: Systematic Review of Qualitative Studies**
Laukka E, Huhtakangas M, Heponiemi T, et al. · Journal of Medical Internet Research, 22(12), e21623

- **Yöntem:** 13 nitel çalışmanın tematik sentezi; sağlık çalışanlarının çevrim içi iletişim deneyimleri.
- **Bulgu:** Erişim ve iletişim faydalarının yanında ek iş yükü, yanlış yorumlama ve yetersiz eğitim sorunları bildirilmiştir.
- **Sınırlılık:** Hasta–profesyonel iletişimi incelenir; bu projenin personeller arası akışına doğrudan etkinlik kanıtı oluşturmaz.
- **Projedeki karşılığı:** Tek alıcı, açık mesaj durumu ve zorunlu sonuç açıklaması kullanılır; acil bildirim hizmeti vaat edilmez.
- DOI: [10.2196/21623](https://doi.org/10.2196/21623)

### [16] · 2025 · İletişim
**Networked Behaviors Associated With a Large-Scale Secure Messaging Network: Cross-Sectional Secondary Data Analysis**
Baratta LR, Xia L, Lew D, et al. · JMIR Medical Informatics, 13, e66544

- **Yöntem:** Bir sağlık sistemindeki altı aylık EHR mesajlaşma verisinin sosyal ağ ve kümeleme analizi.
- **Bulgu:** Mesajlaşma bağlantıları ve davranışları personel rolüne ve çalışma ortamına göre farklılaşmıştır.
- **Sınırlılık:** Tek sağlık sistemi ve tek mesajlaşma platformu incelenmiştir; gözlemsel ilişkiler nedenselliği göstermez.
- **Projedeki karşılığı:** Mesajlarda hasta, gönderen ve alıcı ayrı FK alanlarıdır; görev sorumlusu açıkça belirlenir.
- DOI: [10.2196/66544](https://doi.org/10.2196/66544)

### [17] · 2025 · İzleme
**Clinical benefits and risks of remote patient monitoring: an overview and assessment of methodological rigour of systematic reviews for selected patient groups**
Wartenberg C, Elden H, Frerichs M, et al. · BMC Health Services Research, 25, 133

- **Yöntem:** 16 hasta grubuna ilişkin 84 sistematik derlemenin QUICKSTAR ile yöntemsel değerlendirilmesi.
- **Bulgu:** Yalnızca bir bölümü yeterli yöntemsel düzeye ulaşmıştır; birçok grupta yarar ve riskleri değerlendirecek kanıt sınırlıdır.
- **Sınırlılık:** Sonuçlar seçilmiş gruplar ve derlemelerin kalitesi ile sınırlıdır.
- **Projedeki karşılığı:** Deney sonuçları elde edilmeden fayda yüzdesi yazılmaz; teknik doğrulama ile klinik doğrulama ayrılır.
- DOI: [10.1186/s12913-025-12292-w](https://doi.org/10.1186/s12913-025-12292-w)

### [18] · 2016 · Deneysel çalışma
**Effectiveness of Remote Patient Monitoring After Discharge of Hospitalized Patients With Heart Failure: The Better Effectiveness After Transition–Heart Failure (BEAT-HF) Randomized Clinical Trial**
Ong MK, Romano PS, Edgington S, et al. · JAMA Internal Medicine, 176(3), 310–318

- **Yöntem:** 1437 katılımcıyla telefon desteği ve tele-izlemeyi olağan bakımla karşılaştıran randomize çalışma.
- **Bulgu:** 180 günlük tüm nedenlere bağlı yeniden yatışta anlamlı azalma gösterilmemiştir.
- **Sınırlılık:** Belirli hasta kitlesi ve bakım geçişi müdahalesidir; veritabanı tasarımının başarısını doğrudan ölçmez.
- **Projedeki karşılığı:** Değerlendirmede başlangıç karşılaştırması ve önceden belirlenmiş kabul ölçütleri kullanılır.
- DOI: [10.1001/jamainternmed.2015.7712](https://doi.org/10.1001/jamainternmed.2015.7712)

### [19] · 2018 · Deneysel çalışma
**Efficacy of telemedical interventional management in patients with heart failure (TIM-HF2): a randomised, controlled, parallel-group, unmasked trial**
Koehler F, Koehler K, Deckwart O, et al. · The Lancet, 392(10152), 1047–1057

- **Yöntem:** 1571 hastanın atandığı, yapılandırılmış uzaktan yönetimi olağan bakımla karşılaştıran randomize çalışma.
- **Bulgu:** Tanımlı hasta grubunda plan dışı kardiyovasküler yatış ve tüm nedenlere bağlı ölüm nedeniyle kaybedilen günlerin oranında azalma bildirilmiştir.
- **Sınırlılık:** Sonuç teknoloji, ekip ve bakım sürecinin bütününe aittir; bu küçük prototipe taşınamaz.
- **Projedeki karşılığı:** Ölçüm → doktor incelemesi → sorumlu personele görev → sonuç akışı açıkça modellenir.
- DOI: [10.1016/S0140-6736(18)31880-4](https://doi.org/10.1016/S0140-6736(18)31880-4)

### [20] · 2026 · Kullanılabilirlik
**Digital Health Interventions to Support Chronic Disease Management: Systematic Scoping Review**
Al Mahmud A, Joachim S, Jayaraman PP, et al. · JMIR mHealth and uHealth, 14, e63742

- **Yöntem:** 69 dijital platformun tasarım, geliştirme ve değerlendirme özelliklerinin kapsam derlemesi.
- **Bulgu:** Kısa dönem sonuçlar çoğunlukla olumlu raporlanırken uzun dönem kullanım, teknik sorunlar ve katılım önemli sınırlardır.
- **Sınırlılık:** Birçok çalışma kısa dönemli pilot niteliğindedir; hasta öz yönetimi bu ödevin kapsamından daha geniştir.
- **Projedeki karşılığı:** Az ekranlı tasarım ve görev tabanlı kullanıcı denemeleri tercih edilir; uzun dönem yarar iddiası kurulmaz.
- DOI: [10.2196/63742](https://doi.org/10.2196/63742)

## Literatürden çıkan tasarım kararları

İzleme çalışmalarının sonuçları teknoloji, hasta grubu ve hizmet sürecine göre değişmektedir. Bu nedenle projenin başarısı sağlık sonucunu iyileştirdiği varsayımıyla değil; doğru kayıt, kontrollü erişim ve izlenebilir görev sonucu üzerinden değerlendirilecektir. Ölçüm türü/birim ayrımı veri kalitesini, hasta–personel ataması erişim sınırını, tek alıcılı mesaj ise görev sorumluluğunu desteklemektedir. [4] [10] [12] [14] [16] [19]
