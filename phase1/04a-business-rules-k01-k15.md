> 🇬🇧 **English** · 🇹🇷 Türkçe sürüm aşağıdadır.

# 3.6.1 · Data Modeling Using Entity — Business rules (K01–K15)

The rules define the information in the scenario and the relationships between records. Numeric multiplicities are derived from these sentences. The writing style follows the given [scenario and business rules example](https://github.com/celalceken/DatabaseManagementSystems/blob/master/VYS03.md). This file contains the identity, role, patient–staff assignment and measurement rules.

## Identity and roles

**K01.** Every user has a user ID, username, full name, password hash, role and active flag. The user ID is the primary key; the username is also unique. The password itself is not stored. *(Users)*

**K02.** Every patient has an internal patient ID, a department patient record number, full name and birth date. The internal ID is the primary key; the patient record number is also unique. The birth date cannot be in the future. *(Patients)*

**K03.** A user has exactly one of the roles admin, doctor or nurse. The role is set when the account is created and is not changed later. Administrators manage basic patient information and patient–staff assignments. Doctors and nurses are clinical staff. *(Users)*

**K04.** Patient information is recorded by staff. Patients are not given login accounts; patients and staff are different entities. *(Patients)*

## Patient–staff assignment

**K05.** A patient may have no clinical staff assigned, or one or more doctors or nurses. A doctor or nurse may be assigned to no patient, or to one or more patients. *(PatientStaff)*

**K06.** Each patient–staff assignment belongs to exactly one patient and exactly one staff member. The same patient–staff pair cannot be recorded more than once. The key of the assignment is made of these two IDs. *(PatientStaff)*

**K07.** Only active doctors and nurses can be assigned to patients. An administrator cannot be assigned to a patient as clinical staff. Only current assignments are kept in the assignment table. *(PatientStaff)*

**K08.** Doctors and nurses can view clinical profiles and add measurements only for patients assigned to them. Administrators cannot view clinical measurements or message contents. *(PatientStaff)*

## Measurements

**K09.** Every measurement type has a type ID, name and unit. The type ID is the primary key; the type name is also unique. This project uses body temperature (°C), pulse (bpm), systolic blood pressure (mmHg) and diastolic blood pressure (mmHg). *(MeasurementTypes)*

**K10.** For every measurement, the measurement ID, patient, type, numeric value, observation time, system record time and recording staff member are stored. Measurements are identified by their measurement ID. *(Measurements)*

**K11.** A patient may have no measurements or many measurements. Every measurement must belong to exactly one patient. *(Measurements)*

**K12.** A measurement type may not yet be used in any measurement, or may be used in many. Every measurement must belong to exactly one measurement type; its unit comes from that type. *(MeasurementTypes)*

**K13.** A clinical staff member may have recorded no measurements or many. Every measurement has exactly one recorder. That staff member must be active and assigned to the patient at the time of recording. *(Measurements)*

**K14.** For the four selected types, a measurement value must be positive, less than one million and have at most two decimal places. The observation time cannot be after the record time. The two blood pressure values are stored as two measurements of two different types. *(Measurements)*

**K15.** Recorded measurements are not modified or deleted within this scope. The name and unit of a measurement type that is already in use are not changed, so the meaning of past measurements is preserved. *(Measurements)*

> **Note:** K14 is a data format and record consistency rule; it does not define medical normal ranges.

---

> 🇹🇷 **Türkçe**

# 3.6.1 · Data Modeling Using Entity — İş kuralları (K01–K15)

Kurallar, senaryodaki bilgileri ve kayıtlar arasındaki ilişkileri tanımlar. Sayısal çokluklar bu cümlelerden türetilmiştir. Yazım biçimi, verilen [senaryo ve iş kuralları örneğini](https://github.com/celalceken/DatabaseManagementSystems/blob/master/VYS03.md) izler. Bu dosya kimlik, rol, hasta–personel ataması ve ölçüm kurallarını içerir.

## Kimlik ve roller

**K01.** Her kullanıcının kullanıcı numarası, kullanıcı adı, adı soyadı, parola özeti, rolü ve aktiflik bilgisi bulunur. Kullanıcı numarası birincil anahtardır; kullanıcı adı da benzersizdir. Parolanın kendisi saklanmaz. *(Users)*

**K02.** Her hastanın sistem içi hasta numarası, bölümde kullanılan hasta kayıt numarası, adı soyadı ve doğum tarihi bulunur. Sistem içi numara birincil anahtardır; hasta kayıt numarası da benzersizdir. Doğum tarihi gelecekte olamaz. *(Patients)*

**K03.** Bir kullanıcı yalnızca admin, doctor veya nurse rollerinden birine sahiptir. Rol hesap oluşturulurken belirlenir ve sonradan değiştirilmez. Yönetici kullanıcıları, hasta temel bilgilerini ve hasta–personel atamalarını yönetir. Doktor ve hemşire klinik personeldir. *(Users)*

**K04.** Hasta bilgileri personel tarafından kaydedilir. Hastalara sisteme giriş hesabı açılmaz; hasta ile personel farklı varlıklardır. *(Patients)*

## Hasta–personel ataması

**K05.** Bir hastaya hiçbir klinik personel atanmamış olabileceği gibi bir veya birden fazla doktor ya da hemşire atanmış da olabilir. Bir doktor veya hemşire de hiçbir hastaya atanmamış olabileceği gibi bir veya birden fazla hastaya atanabilir. *(PatientStaff)*

**K06.** Her hasta–personel ataması yalnızca bir hastaya ve yalnızca bir personele aittir. Aynı hasta ve aynı personel çifti birden fazla kez kaydedilemez. Atama kaydının anahtarı bu iki numaradan oluşur. *(PatientStaff)*

**K07.** Yalnızca aktif doktor ve hemşireler hastalara atanabilir. Yönetici hastaya klinik personel olarak atanamaz. Atama tablosunda yalnızca güncel atamalar tutulur. *(PatientStaff)*

**K08.** Doktor ve hemşire yalnızca kendilerine atanmış hastaların klinik profillerini görebilir ve ölçüm ekleyebilir. Yönetici klinik ölçüm ve mesaj içeriklerini görüntüleyemez. *(PatientStaff)*

## Ölçümler

**K09.** Her ölçüm türünün tür numarası, adı ve birimi bulunur. Tür numarası birincil anahtardır; tür adı da benzersizdir. Bu projede vücut sıcaklığı (°C), nabız (bpm), sistolik kan basıncı (mmHg) ve diyastolik kan basıncı (mmHg) kullanılır. *(MeasurementTypes)*

**K10.** Her ölçümün ölçüm numarası, ait olduğu hasta, türü, sayısal değeri, gözlem zamanı, sisteme kayıt zamanı ve kaydeden personeli saklanır. Ölçümler ölçüm numarasıyla ayırt edilir. *(Measurements)*

**K11.** Bir hastanın hiç ölçümü bulunmayabileceği gibi birden fazla ölçümü de bulunabilir. Her ölçüm yalnızca bir hastaya ait olmak zorundadır. *(Measurements)*

**K12.** Bir ölçüm türü henüz hiçbir ölçümde kullanılmamış olabileceği gibi birden fazla ölçümde kullanılabilir. Her ölçüm yalnızca bir ölçüm türüne ait olmak zorundadır; birimi bu türden alınır. *(MeasurementTypes)*

**K13.** Bir klinik personel hiç ölçüm kaydetmemiş olabileceği gibi birden fazla ölçüm kaydedebilir. Her ölçümü kaydeden yalnızca bir personel bulunur. Bu personel kayıt anında aktif ve ilgili hastaya atanmış olmalıdır. *(Measurements)*

**K14.** Ölçüm değeri seçilen dört tür için pozitif, bir milyondan küçük ve en çok iki ondalık basamaklı olmalıdır. Gözlem zamanı kayıt zamanından sonra olamaz. Tansiyonun iki değeri, iki farklı türde iki ölçüm olarak saklanır. *(Measurements)*

**K15.** Kaydedilmiş ölçümler bu kapsamda değiştirilmez veya silinmez. Kullanılmış ölçüm türünün adı ve birimi değiştirilmez; böylece geçmiş ölçümlerin anlamı korunur. *(Measurements)*

> **Not:** K14 veri biçimi ve kayıt tutarlılığı kuralıdır; tıbbi normal değer aralığı belirlemez.
