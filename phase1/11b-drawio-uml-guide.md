> 🇬🇧 **English** · 🇹🇷 Türkçe sürüm aşağıdadır.

# Appendix B · Drawing the UML class diagram in draw.io and exporting

These steps create the UML class diagram in the same `phase1/diagrams/er-uml.drawio` file after the ER page, and export the drawings.

1. **Create the UML page.** Add a new page and name it UML. Open the UML or UML 2.5 library under More Shapes. Place the six classes in the Figure 2 layout. Write the class name, typed attributes and behaviours in the three compartments. Use the names User, Patient, PatientStaff, MeasurementType, Measurement and Message.

2. **Complete the UML attributes and multiplicities.** Copy the attributes from Figure 2; use − for passwordHash and + for the other attributes and behaviours. Mark Message.resultText and completedAt with ? to show that they may be empty. Keep the eight plain association lines and the **1 / 0..*** values at their ends; do not add crow’s feet to UML lines. Sender and recipient must remain separate; this model needs no inheritance arrow or composition diamond.

3. **Save and export.** Save the editable .drawio source with File → Save As. Export the image with File → Export as → SVG or PDF. Check the six boxes and eight relationships, the PK/FK marks, the end multiplicities and that no text is cut off. Caption the ER image “Figure 1” and the UML image “Figure 2”.

Menu reference: [exporting](https://www.drawio.com/docs/manual/export/export-diagram/). Menu language may vary with your settings.

---

> 🇹🇷 **Türkçe**

# Ek B · UML sınıf diyagramını draw.io’da çizmek ve dışa aktarmak

Bu adımlar, ER sayfasının ardından UML sınıf diyagramını aynı `phase1/diagrams/er-uml.drawio` dosyasında oluşturmak ve çizimleri dışa aktarmak içindir.

1. **UML sayfasını oluştur.** Yeni sayfa ekle ve adını UML yap. More Shapes içinde UML veya UML 2.5 kütüphanesini aç. Altı sınıfı Şekil 2 düzeninde yerleştir. Üç bölüme sırasıyla sınıf adı, tipli alanlar ve davranışları yaz. User, Patient, PatientStaff, MeasurementType, Measurement ve Message adlarını kullan.

2. **UML alanlarını ve çokluklarını tamamla.** Alanları Şekil 2’den aktar; passwordHash için −, diğer özellikler ve davranışlar için + kullan. Message.resultText ve completedAt alanlarında ? işaretiyle boş değer olasılığını göster. UML’de sekiz normal association çizgisini ve uçlardaki **1 / 0..*** değerlerini koru; UML çizgilerine karga ayağı ekleme. Gönderen ve alıcı yine ayrı olmalıdır; bu modelde kalıtım oku veya composition elması gerekmez.

3. **Kaydet ve dışa aktar.** File → Save As ile düzenlenebilir .drawio kaynağını kaydet. File → Export as → SVG veya PDF ile görsel çıktıyı al. Altı kutu ve sekiz ilişkiyi, PK/FK işaretlerini, uç çokluklarını ve yazıların kesilmediğini kontrol et. ER görseline “Şekil 1”, UML görseline “Şekil 2” açıklamasını ekle.

Menü başvurusu: [dışa aktarma](https://www.drawio.com/docs/manual/export/export-diagram/). Menülerin dili kullanılan ayara göre değişebilir.
