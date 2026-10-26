> 🇬🇧 **English** · 🇹🇷 Türkçe sürüm aşağıdadır.

# 3.6.1 · Data Modeling Using Entity — Business rules (K16–K24)

This file contains the task message state flow and the record integrity rules.

## Messages

**K16.** Every message has a message ID, related patient, sender, recipient, text, creation time, status, result note and completion time. Messages are identified by their message ID. *(Messages)*

**K17.** A patient may have no messages or many messages. Every message must relate to exactly one patient. *(Messages)*

**K18.** A doctor may have sent no messages or many. Every message has exactly one sender, and the sender must be a doctor. Nurses and administrators cannot send messages. *(Messages)*

**K19.** A doctor or nurse may have received no messages or many. Every message has exactly one recipient. The sender and recipient must be different people and must both be actively assigned to the same patient at the time of sending. *(Messages)*

**K20.** A new message is created in the Pending status; the result note and completion time are empty. The message text cannot be empty and can be at most 1,000 characters. *(Messages)*

**K21.** Only the recipient, with an active account and a current patient assignment, can move a message to Completed. This requires a non-empty result note of 1–1,000 characters and a completion time. The completion time cannot be earlier than the creation time. A completed message cannot be completed again or returned to Pending. *(Messages)*

**K22.** A message's content can be viewed by its sender or recipient while they have current access to the related patient. Other staff assigned to the same patient do not gain the right to see all messages because of that assignment. *(Messages)*

## Record integrity

**K23.** Patients, users and measurement types that have dependent records such as measurements or messages cannot be deleted. Staff accounts can be deactivated; past records are preserved. *(Users)*

**K24.** A staff member's account cannot be deactivated, and their assignment to the related patient cannot be removed, while a pending message addressed to them exists. The assignment can be removed after the tasks are completed. Removing an assignment does not delete past records; it ends current access. *(PatientStaff)*

> **Note:** Role and assignment rules cannot be enforced by foreign keys alone; they are also checked in the transaction algorithms.

---

> 🇹🇷 **Türkçe**

# 3.6.1 · Data Modeling Using Entity — İş kuralları (K16–K24)

Bu dosya görev mesajlarının durum akışını ve kayıt bütünlüğü kurallarını içerir.

## Mesajlar

**K16.** Her mesajın mesaj numarası, ilgili hastası, göndereni, alıcısı, metni, oluşturulma zamanı, durumu, sonuç açıklaması ve tamamlanma zamanı bulunur. Mesajlar mesaj numarasıyla ayırt edilir. *(Messages)*

**K17.** Bir hasta hakkında hiç mesaj bulunmayabileceği gibi birden fazla mesaj bulunabilir. Her mesaj yalnızca bir hastayla ilgili olmak zorundadır. *(Messages)*

**K18.** Bir doktor hiç mesaj göndermemiş olabileceği gibi birden fazla mesaj gönderebilir. Her mesajın yalnızca bir göndereni vardır ve gönderen doktor olmalıdır. Hemşire ve yönetici mesaj gönderemez. *(Messages)*

**K19.** Bir doktor veya hemşire hiç mesaj almamış olabileceği gibi birden fazla mesaj alabilir. Her mesajın yalnızca bir alıcısı bulunur. Gönderen ve alıcı farklı kişiler olmalı ve gönderim anında aktif olarak aynı hastaya atanmış bulunmalıdır. *(Messages)*

**K20.** Yeni mesaj Bekliyor (Pending) durumunda oluşturulur; sonuç açıklaması ve tamamlanma zamanı boştur. Mesaj metni boş olamaz ve en fazla 1.000 karakter olabilir. *(Messages)*

**K21.** Mesajı yalnızca alıcısı, aktif hesabı ve güncel hasta ataması varsa Tamamlandı (Completed) durumuna getirebilir. Bu işlemde 1–1.000 karakterlik boş olmayan sonuç açıklaması ve tamamlanma zamanı zorunludur. Tamamlanma zamanı oluşturulma zamanından önce olamaz. Tamamlanmış mesaj yeniden tamamlanamaz veya beklemeye alınamaz. *(Messages)*

**K22.** Bir mesajın içeriğini, ilgili hastaya güncel erişimi olan gönderen veya alıcı görebilir. Aynı hastaya atanmış başka personel bu nedenle tüm mesajları görme hakkı kazanmaz. *(Messages)*

## Kayıt bütünlüğü

**K23.** Ölçüm veya mesaj gibi bağlı kayıtları bulunan hasta, kullanıcı ve ölçüm türü silinemez. Personel hesabı pasifleştirilebilir; geçmiş kayıtlar korunur. *(Users)*

**K24.** Bir personelin alıcı olduğu bekleyen mesaj varken hesabı pasifleştirilemez; ilgili hastadaki ataması kaldırılamaz. Görevler tamamlandıktan sonra atama kaldırılabilir. Atamanın kaldırılması geçmiş kayıtları silmez, güncel erişimi sonlandırır. *(PatientStaff)*

> **Not:** Rol ve atama kuralları yalnız yabancı anahtarlarla sağlanamaz; işlem algoritmalarında ayrıca kontrol edilir.
