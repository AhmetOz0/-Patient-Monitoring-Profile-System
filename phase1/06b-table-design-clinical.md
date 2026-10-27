> 🇬🇧 **English** · 🇹🇷 Türkçe sürüm aşağıdadır.

# 3.6.3 · Table Design — MeasurementTypes, Measurements, Messages and normalization

**All fields except result_text and completed_at are required.** These two fields are empty only for pending messages.

## MeasurementTypes · `measurement_types` (3 fields)

Name and unit of the four measurement types.

**Table 7. MeasurementTypes fields**

| Field | Data type | Key / constraint |
|---|---|---|
| `type_id` | BIGINT identity | PK; automatic |
| `name` | VARCHAR(60) | UQ; required |
| `unit` | VARCHAR(20) | Required; unchanged once the type is used |

## Measurements · `measurements` (7 fields)

Each observation is a separate row; the unit comes from the measurement type.

**Table 8. Measurements fields**

| Field | Data type | Key / constraint |
|---|---|---|
| `measurement_id` | BIGINT identity | PK; automatic |
| `patient_id` | BIGINT | FK Patients; required |
| `type_id` | BIGINT | FK MeasurementTypes; required |
| `recorded_by` | BIGINT | FK Users; from the session |
| `value` | NUMERIC(8,2) | 0 < value < 1,000,000; at most 2 decimals |
| `observed_at` | TIMESTAMPTZ | Required; observed_at ≤ recorded_at |
| `recorded_at` | TIMESTAMPTZ | Server: CURRENT_TIMESTAMP |

## Messages · `messages` (9 fields)

Text, status and result of a single-recipient task.

**Table 9. Messages fields**

| Field | Data type | Key / constraint |
|---|---|---|
| `message_id` | BIGINT identity | PK; automatic |
| `patient_id` | BIGINT | FK Patients; required |
| `sender_id` | BIGINT | FK Users; assigned doctor |
| `recipient_id` | BIGINT | FK Users; assigned doctor/nurse |
| `body` | VARCHAR(1000) | 1–1000 characters; cannot be blank |
| `status` | VARCHAR(10) | Pending / Completed; default Pending |
| `result_text` | VARCHAR(1000) | Pending: NULL; Completed: filled |
| `created_at` | TIMESTAMPTZ | Server: CURRENT_TIMESTAMP |
| `completed_at` | TIMESTAMPTZ | Pending: NULL; Completed: required |

## Keys and normalization

**Table 10. Functional dependencies and their effect on the design**

| Table | Dependency | Result |
|---|---|---|
| Users | user_id → other user fields; username is a candidate key | Staff names are not repeated in transaction records. |
| Patients | patient_id → patient_no, full_name, birth_date; patient_no is a candidate key | Age is not stored separately; the birth date is used. |
| PatientStaff | (patient_id, user_id) composite key | No non-key fields; staff information is not moved into this table. |
| MeasurementTypes | type_id → name, unit; name is a candidate key | Type and unit are defined in one place. |
| Measurements | measurement_id → other measurement fields | Type name and unit are not copied into this table. |
| Messages | message_id → other message fields | Sender and recipient names are obtained through Users. |

Fields are single-valued; a cell never holds a staff list or two readings such as “120/80”. Under the stated dependencies there is no partial dependency in the composite-key PatientStaff table and no transitive dependency between non-key fields in the other tables. Under these business rules the design satisfies **3NF**. The fact that the message status makes the result field mandatory does not mean that all Completed messages have the same result text.

Foreign keys prevent records from being created with a non-existent patient, staff or type ID. Deleting parent records with dependents is restricted with the RESTRICT approach. The user’s role, active status and current assignment are checked in the application transaction. Keeping old versions of patient and staff names is not required in this scope.

---

> 🇹🇷 **Türkçe**

# 3.6.3 · Table Design — MeasurementTypes, Measurements, Messages ve normalizasyon

**result_text ve completed_at dışında tüm alanlar zorunludur.** Bu iki alan yalnız bekleyen mesajlarda boştur.

## MeasurementTypes · `measurement_types` (3 alan)

Dört ölçüm türünün adı ve birimi.

**Tablo 7. MeasurementTypes alanları**

| Alan | Veri tipi | Anahtar / kısıt |
|---|---|---|
| `type_id` | BIGINT identity | PK; otomatik |
| `name` | VARCHAR(60) | UQ; zorunlu |
| `unit` | VARCHAR(20) | Zorunlu; kullanılan türde değişmez |

## Measurements · `measurements` (7 alan)

Her gözlem ayrı satırdır; birim ölçüm türünden alınır.

**Tablo 8. Measurements alanları**

| Alan | Veri tipi | Anahtar / kısıt |
|---|---|---|
| `measurement_id` | BIGINT identity | PK; otomatik |
| `patient_id` | BIGINT | FK Patients; zorunlu |
| `type_id` | BIGINT | FK MeasurementTypes; zorunlu |
| `recorded_by` | BIGINT | FK Users; oturumdan |
| `value` | NUMERIC(8,2) | 0 < değer < 1.000.000; en çok 2 ondalık |
| `observed_at` | TIMESTAMPTZ | Zorunlu; observed_at ≤ recorded_at |
| `recorded_at` | TIMESTAMPTZ | Sunucu: CURRENT_TIMESTAMP |

## Messages · `messages` (9 alan)

Tek alıcılı görevin metni, durumu ve sonucu.

**Tablo 9. Messages alanları**

| Alan | Veri tipi | Anahtar / kısıt |
|---|---|---|
| `message_id` | BIGINT identity | PK; otomatik |
| `patient_id` | BIGINT | FK Patients; zorunlu |
| `sender_id` | BIGINT | FK Users; atanmış doktor |
| `recipient_id` | BIGINT | FK Users; atanmış doktor/hemşire |
| `body` | VARCHAR(1000) | 1–1000 karakter; boşluk olamaz |
| `status` | VARCHAR(10) | Pending / Completed; varsayılan Pending |
| `result_text` | VARCHAR(1000) | Pending: NULL; Completed: dolu |
| `created_at` | TIMESTAMPTZ | Sunucu: CURRENT_TIMESTAMP |
| `completed_at` | TIMESTAMPTZ | Pending: NULL; Completed: zorunlu |

## Anahtarlar ve normalizasyon

**Tablo 10. Fonksiyonel bağımlılıklar ve tasarımdaki karşılıkları**

| Tablo | Bağımlılık | Sonuç |
|---|---|---|
| Users | user_id → diğer kullanıcı alanları; username aday anahtar | Personel adı işlem kayıtlarında tekrarlanmaz. |
| Patients | patient_id → patient_no, full_name, birth_date; patient_no aday anahtar | Yaş ayrıca saklanmaz; doğum tarihi kullanılır. |
| PatientStaff | (patient_id, user_id) birleşik anahtar | Anahtar dışı alan yoktur; bir personele ait bilgiler bu tabloya taşınmaz. |
| MeasurementTypes | type_id → name, unit; name aday anahtar | Tür ve birimi tek noktada tanımlanır. |
| Measurements | measurement_id → diğer ölçüm alanları | Tür adı ve birim bu tabloya kopyalanmaz. |
| Messages | message_id → diğer mesaj alanları | Gönderen ve alıcının adları Users üzerinden elde edilir. |

Alanlar tek değerlidir; bir hücrede personel listesi veya “120/80” biçiminde iki ölçüm tutulmaz. Birleşik anahtarlı PatientStaff’ta kısmi bağımlılık, diğer tablolarda belirtilen bağımlılıklar altında anahtar dışı alanlar arasında geçişli bağımlılık bulunmaz. Tasarım bu iş kuralları altında **3NF** koşullarını sağlar. Mesaj durumunun sonuç alanını zorunlu kılması, bütün Completed mesajların aynı sonuç metnine sahip olması anlamına gelmez.

Yabancı anahtarlar var olmayan hasta, personel veya tür numarasıyla kayıt oluşturulmasını engeller. Bağlı kayıtların silinmesi RESTRICT yaklaşımıyla sınırlandırılır. Kullanıcının rolü, aktifliği ve güncel ataması ise uygulama işleminde denetlenir. Hasta ve personel adlarının eski sürümlerini tutma gereksinimi bu kapsamda yoktur.
