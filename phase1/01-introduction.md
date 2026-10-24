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
