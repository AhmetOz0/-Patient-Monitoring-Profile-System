> 🇬🇧 **English** · 🇹🇷 Türkçe sürüm aşağıdadır.

# 3.6.5 · Indexing Structures — Index design

Because the measurement history uses patient equality and a time range, and the task inbox uses a recipient/status filter and time ordering, four secondary **B-tree** indexes are planned. Column order was chosen for these queries. ([PostgreSQL multicolumn index documentation](https://www.postgresql.org/docs/18/indexes-multicolumn.html))

**Table 11. Indexes selected for the project**

| Index | Columns · left to right | Supported operation |
|---|---|---|
| ix_patient_staff_user | user_id, patient_id | Q1 and Q4: from a staff member to assigned patients. |
| ix_measurements_history | patient_id, observed_at DESC, measurement_id DESC | Q2: patient/time filter and stable measurement order. |
| ix_messages_inbox | recipient_id, status, created_at DESC, message_id DESC | Q3: recipient’s pending tasks, newest first. |
| ix_messages_patient | patient_id, created_at DESC, message_id DESC | Q5: a patient’s messages; the sender/recipient condition is applied separately. |

The PatientStaff primary key starts with `(patient_id, user_id)`; for Q1 the reverse `(user_id, patient_id)` access is planned separately. Indexes provided by the uniqueness of Users.username, Patients.patient_no and MeasurementTypes.name and by the PK columns are not created again.

Indexes take extra space and are updated when new records are written. For this reason an index is not proposed for every column. On small data sets a sequential scan may be appropriate. The real plan and timing will be measured in the experiment environment with `EXPLAIN (ANALYZE, BUFFERS)`; no speed-up percentage is given here. ([PostgreSQL query plan documentation](https://www.postgresql.org/docs/18/using-explain.html))

---

> 🇹🇷 **Türkçe**

# 3.6.5 · Indexing Structures — İndeks tasarımı

Ölçüm geçmişinde hasta eşitliği ve zaman aralığı, görev kutusunda alıcı/durum filtresi ve zaman sırası kullanıldığı için dört ikincil **B-tree** indeksi planlanmıştır. Sütun sırası bu sorgulara göre belirlenmiştir. ([PostgreSQL çok sütunlu indeks belgesi](https://www.postgresql.org/docs/18/indexes-multicolumn.html))

**Tablo 11. Proje için seçilen indeksler**

| İndeks | Alanlar · soldan sağa | Desteklediği işlem |
|---|---|---|
| ix_patient_staff_user | user_id, patient_id | Q1 ve Q4: personelden atanmış hastalara erişim. |
| ix_measurements_history | patient_id, observed_at DESC, measurement_id DESC | Q2: hasta/zaman filtresi ve kararlı ölçüm sırası. |
| ix_messages_inbox | recipient_id, status, created_at DESC, message_id DESC | Q3: alıcının bekleyen görevleri, yeniden eskiye. |
| ix_messages_patient | patient_id, created_at DESC, message_id DESC | Q5: hastanın mesajları; gönderen/alıcı koşulu ayrıca uygulanır. |

PatientStaff birincil anahtarı `(patient_id, user_id)` ile başlar; Q1 için bunun ters yönündeki `(user_id, patient_id)` erişimi ayrıca planlanmıştır. Users.username, Patients.patient_no ve MeasurementTypes.name benzersizliği ile PK alanlarının indeksleri tekrar oluşturulmaz.

İndeksler ek alan kaplar ve yeni kayıt yazılırken güncellenir. Bu nedenle her sütuna indeks önerilmemiştir. Küçük veri kümelerinde ardışık tarama uygun olabilir. Gerçek plan ve süre `EXPLAIN (ANALYZE, BUFFERS)` ile deney ortamında ölçülecektir; burada hızlanma yüzdesi verilmemiştir. ([PostgreSQL sorgu planı belgesi](https://www.postgresql.org/docs/18/using-explain.html))
