> 🇬🇧 **English** · 🇹🇷 Türkçe sürüm aşağıdadır.

# Appendix A · Drawing the ER diagram in draw.io

These steps reproduce and edit the project’s Crow’s Foot ER diagram in draw.io. The editable source is `phase1/diagrams/er-uml.drawio`.

1. **Create a file or open the existing drawing.** [Open draw.io](https://app.diagrams.net/). For a new drawing choose Device → Create New Diagram → Blank Diagram. To edit the existing drawing, open `er-uml.drawio` with File → Open From → Device. The file has two pages, ER and UML.

2. **Place the six tables on the ER page.** Open the table shapes with More Shapes → Software → Entity Relation → Apply. Place Users, PatientStaff, Patients in the top row from left to right, and Messages, Measurements, MeasurementTypes in the bottom row. This layout matches Figure 1.

3. **Write the fields and keys.** Copy the fields from the table design into the shapes. Mark user_id, patient_id, type_id, measurement_id and message_id as PK in their own parent tables. In PatientStaff mark both patient_id and user_id as PK/FK. Write UQ next to username, patient_no and the type name. If a field does not fit, add a row or enlarge the box.

4. **Choose the Crow’s Foot line ends.** Connect the eight mappings from the ER relationships table one by one. Use the “1 mandatory to many optional” connector from the Entity Relation library, or select the line and set the start/end markers in the Style panel. If you draw from the parent to the dependent table, the start must be **exactly one (double bar)** and the end **zero or many (circle and crow’s foot)**. If you drew in the opposite direction, swap the ends. For example, there is a double bar next to Patients and a circle and crow’s foot next to Measurements.

5. **Set solid and dashed lines.** Draw Users–PatientStaff and Patients–PatientStaff as **solid** lines: the parent key is part of PatientStaff’s composite PK. Draw the other six links as **dashed** lines: the FK is not part of the dependent table’s PK. Select the line and change it in Style → Line. Keep the end markers while doing this; a dashed line does not make a mandatory relationship optional.

6. **Separate the sender and recipient lines.** Draw two separate dashed lines between Users and Messages: “sender” for Users.user_id → Messages.sender_id and “recipient” for Users.user_id → Messages.recipient_id. On both lines the Users end must be a double bar and the Messages end a circle and crow’s foot. Label the Users–Measurements line “recorded by”. Route the bends outside the boxes; do not mark crossings as connection points.

Menu references: [opening files](https://www.drawio.com/docs/manual/open-diagram-file/) · [Entity Relation shapes](https://www.drawio.com/docs/diagram-types/entity-relationship-tables/) · [Crow’s Foot markers](https://www.drawio.com/docs/tutorials/crows-foot-notation/). Menu language may vary with your settings.

---

> 🇹🇷 **Türkçe**

# Ek A · ER diyagramını draw.io’da çizmek

Bu adımlar projedeki Crow’s Foot ER diyagramını draw.io’da yeniden üretmek ve düzenlemek içindir. Düzenlenebilir kaynak `phase1/diagrams/er-uml.drawio` dosyasıdır.

1. **Dosyayı oluştur veya hazır çizimi aç.** [draw.io’yu aç](https://app.diagrams.net/). Yeni çalışma için Device → Create New Diagram → Blank Diagram seç. Hazır çizimi düzenlemek için `er-uml.drawio` dosyasını File → Open From → Device ile aç. Dosyada ER ve UML adında iki sayfa vardır.

2. **ER sayfasına altı tabloyu yerleştir.** More Shapes → Software → Entity Relation → Apply ile tablo şekillerini aç. Üst sıraya soldan sağa Users, PatientStaff, Patients; alt sıraya Messages, Measurements, MeasurementTypes yerleştir. Bu düzen Şekil 1 ile aynıdır.

3. **Alanları ve anahtarları yaz.** Tablo tasarımındaki alanları ilgili şekillere aktar. user_id, patient_id, type_id, measurement_id ve message_id alanlarını kendi ana tablolarında PK işaretle. PatientStaff’ta patient_id ve user_id satırlarının ikisini de PK/FK işaretle. username, patient_no ve tür name alanlarına UQ yaz. Alan sığmazsa satır ekle veya kutuyu büyüt.

4. **Crow’s Foot bağlantı uçlarını seç.** ER ilişkileri tablosundaki sekiz eşleşmeyi sırayla bağla. Entity Relation kütüphanesinden “1 mandatory to many optional” bağlantısını kullan veya çizgiyi seçip Style bölümündeki başlangıç/bitiş uçlarını ayarla. Ana tablodan bağlı tabloya çiziyorsan başlangıç **tam bir (çift çizgi)**, bitiş **sıfır veya çok (daire ve karga ayağı)** olmalıdır. Ters yönde çizdiysen uçları ters seç. Örneğin Patients yanında çift çizgi, Measurements yanında daire ve karga ayağı bulunur.

5. **Düz ve kesikli çizgileri ayarla.** Users–PatientStaff ve Patients–PatientStaff bağlantılarını **düz** çiz: ana tablonun anahtarı PatientStaff’ın birleşik PK’sine katılır. Diğer altı bağlantıyı **kesikli** çiz: FK alanı bağlı tablonun PK’sinde değildir. Çizgiyi seçip Style → Line ayarından düz/kesikli biçimi değiştir. Uç sembollerini bu işlem sırasında koru; kesikli çizgi zorunlu ilişkiyi isteğe bağlı yapmaz.

6. **Gönderen ve alıcı çizgilerini ayır.** Users ile Messages arasında iki ayrı kesikli çizgi çiz: Users.user_id → Messages.sender_id için “gönderen”, Users.user_id → Messages.recipient_id için “alıcı”. Her iki çizgide Users tarafı çift çizgi, Messages tarafı daire ve karga ayağı olmalıdır. Users–Measurements çizgisine “kaydeden” yaz. Dirsekleri kutuların dışından geçir; kesişimleri bağlantı noktası gibi işaretleme.

Menü başvuruları: [dosya açma](https://www.drawio.com/docs/manual/open-diagram-file/) · [Entity Relation şekilleri](https://www.drawio.com/docs/diagram-types/entity-relationship-tables/) · [Crow’s Foot uç sembolleri](https://www.drawio.com/docs/tutorials/crows-foot-notation/). Menülerin dili kullanılan ayara göre değişebilir.
