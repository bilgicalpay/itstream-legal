# RDC ITStream gizlilik bildirimi

Sürüm 1.0 · 6 Kasım 2026

Bu bildirim, Azure DevOps eklentisi "RDC ITStream" ile bağımsız RDC ITStream Sihirbazının (bundan sonra "Ürün") hangi verileri nerede sakladığını ve RDC Partner'a (bundan sonra "RDC") neleri gönderdiğini açıklar.

## 1. Veri sorumlusu

- Müşterinin Azure DevOps kurumunda oluşturduğu ve işlediği verilerin sorumlusu Müşteridir. RDC bu verilere erişmez.
- Lisans başvurusu ve iletişim için RDC'ye iletilen bilgilerin sorumlusu RDC Partner'dır. İletişim: it4it@rdc.com.tr

## 2. Müşterinin Azure DevOps kurumunda saklanan veriler

Ürün çalışması için gereken verileri Müşterinin kendi Azure DevOps kurumunda saklar ve RDC'nin sunucularına aktarmaz:

- İş öğeleri, alanlar, bağlantılar ve Discussion yorumları (Azure DevOps'un kendi deposu).
- Ayarlar, ArchiMate modeli, denetim kayıtları, maliyet kataloğu ve benzeri belgeler (Azure DevOps eklenti verisi deposu; kurum, proje ya da kullanıcı kapsamında).
- Lisans belgesi: lisans anahtarı, lisans sunucusu adresi ve önceki anahtarların parmak izleri.
- Etkin kullanıcı sayımı: her kullanıcı için tuzlu SHA-256 özetinden üretilen takma kimlik ve modüllerin son kullanım günleri. Ad, e-posta ya da açık kullanıcı kimliği yazılmaz.
- Bağlantıların gizli değerleri (parola, token) Azure Pipelines Library değişken gruplarında gizli değer olarak tutulur; Ürün bunları eklenti verisine yazmaz.

Bağımsız sihirbaz verileri yalnız kullanıcının tarayıcısında (tarayıcı deposu) ya da kullanıcının indirdiği dosyalarda tutar.

## 3. Lisans denetimi ve RDC'ye gönderilen veriler

- Lisans anahtarı Ürünün içinde, RDC'nin açık anahtarıyla doğrulanır. Doğrulama için RDC'ye istek gönderilmez.
- Etkin kullanıcı ve modül kullanım sayıları Müşterinin kurumunda kalır. Ürünün bu sürümü RDC'ye kullanım bildirimi göndermez. İleride isteğe bağlı bir kullanım bildirimi eklenirse bildirim yalnız lisans kimliğini, Azure DevOps kurumunun ya da sunucusunun adını, etkin kullanıcı sayısını, eklentinin sürümünü ve dönemi taşıyacak, varsayılan olarak kapalı olacak ve bu bildirim güncellenecektir.
- Kurum yöneticisi deneme ya da ücretsiz lisans istediğinde Ürün, RDC'nin lisans sunucusuna (varsayılan https://gotime.higgscloud.com) yalnız şunları gönderir: Azure DevOps kurumunun ya da sunucusunun adı, eklentinin sürümü ve yöneticinin isteğe bağlı olarak yazdığı şirket adı, kişi adı ve e-posta adresi.
- Ücretsiz lisans başvuru formu lisans sunucusunda yeni sekmede açılır; formun kurum adı alanı önceden doldurulur, başka kişi bilgisi gönderilmez.

## 4. Yapay zekâ özellikleri

- Yapay zekâ özellikleri yalnız Müşteri bir sağlayıcı (ör. Azure OpenAI, OpenAI uyumlu servis, Anthropic) yapılandırdığında çalışır.
- İstekler kullanıcının tarayıcısından doğrudan Müşterinin yapılandırdığı adrese gider; RDC'nin sunucularından geçmez. İstekte, kullanıcının sorusu ve ilgili iş öğesinin verisi gibi işi yapmak için gereken içerik bulunur.
- Kişisel token kullanıcı kapsamlı eklenti verisinde tutulur ve yalnız kullanıcının kendisi okur. Token günlüğe, iş öğesine, Discussion'a ya da Git'e yazılmaz.
- Sağlayıcının veriyi nasıl işlediği Müşterinin o sağlayıcıyla yaptığı sözleşmeye tabidir.

## 5. Diğer üçüncü taraf bağlantıları

Müşteri Ürünü test platformu, kayıt sistemleri (ör. ITSM, CMDB, GRC) ya da dizin hizmeti gibi sistemlere bağlarsa veri, Müşterinin yapılandırdığı adrese doğrudan gönderilir. Bu sistemlerdeki işleme, Müşterinin o sistemlerle yaptığı sözleşmelere tabidir.

## 6. Saklama süresi

- Müşterinin kurumundaki veriler, Müşteri silene ya da eklentiyi ve verisini kaldırana kadar Azure DevOps'ta kalır.
- RDC'ye lisans başvurusuyla iletilen bilgiler lisans ilişkisi süresince ve yürürlükteki mevzuatın öngördüğü süre boyunca saklanır, sonra silinir ya da anonim hâle getirilir.

## 7. Verinin korunması ve sorumluluk

Ürünün verisi Azure DevOps Services kullanıldığında Microsoft'un sistemlerinde, Azure DevOps Server kullanıldığında Müşterinin kendi yönettiği sunucularda barındırılır. Verinin yedeklenmesi, saklanması, silinmesi ve korunması Müşterinin ve barındırma hizmetini sağlayanın sorumluluğundadır; RDC bu konularda ve bu sistemlerde meydana gelen güvenlik ihlallerinde sorumluluk kabul etmez. Ayrıntılar son kullanıcı lisans sözleşmesinin "Sorumluluk reddi" bölümündedir.

## 8. Haklarınız

KVKK ve uygulanabildiği ölçüde GDPR kapsamında kişisel verilerinize erişme, düzeltme, silme, işlemeyi kısıtlama, itiraz etme ve veri taşınabilirliği haklarınız vardır. Taleplerinizi it4it@rdc.com.tr adresine iletin. Müşterinin Azure DevOps kurumundaki verilerle ilgili talepler için kurumunuzun yöneticisine başvurun.

## 9. Değişiklikler

RDC bu bildirimi güncelleyebilir. Güncel sürüm Ürünle ve Marketplace sayfasıyla yayımlanır.

---

# RDC ITStream privacy notice

Version 1.0 · 6 November 2026

This notice explains which data the Azure DevOps extension "RDC ITStream" and the standalone RDC ITStream Wizard ("Product") store and where, and what they send to RDC Partner ("RDC").

## 1. Data controller

- The Customer is the controller of the data it creates and processes in its Azure DevOps organization. RDC has no access to this data.
- RDC Partner is the controller of the information sent to RDC for license applications and contact. Contact: it4it@rdc.com.tr

## 2. Data stored in the Customer's Azure DevOps organization

The Product stores the data it needs in the Customer's own Azure DevOps organization and does not transfer it to RDC's servers:

- Work items, fields, links and Discussion comments (Azure DevOps' own store).
- Settings, the ArchiMate model, audit records, the cost catalog and similar documents (the Azure DevOps extension data store; at organization, project or user scope).
- The license document: the license key, the license server address and fingerprints of previous keys.
- Active user counting: for each user, a pseudonymous identifier derived from a salted SHA-256 hash and the last days the modules were used. No name, e-mail address or plain user ID is written.
- Secret values of connections (passwords, tokens) are kept as secret values in Azure Pipelines Library variable groups; the Product does not write them to extension data.

The standalone wizard keeps data only in the user's browser (browser storage) or in files the user downloads.

## 3. License check and data sent to RDC

- The license key is verified inside the Product with RDC's public key. No request is sent to RDC for verification.
- Active user and module usage counts stay in the Customer's organization. This version of the Product sends no usage report to RDC. If an optional usage report is added in the future, it will carry only the license ID, the name of the Azure DevOps organization or server, the number of active users, the extension version and the period; it will be off by default and this notice will be updated.
- When an organization administrator requests a trial or free license, the Product sends to RDC's license server (by default https://gotime.higgscloud.com) only: the name of the Azure DevOps organization or server, the extension version and the company name, contact name and e-mail address the administrator optionally enters.
- The free license application form opens on the license server in a new tab; the organization name field is pre-filled and no other personal information is sent.

## 4. AI features

- AI features work only when the Customer configures a provider (for example Azure OpenAI, an OpenAI-compatible service or Anthropic).
- Requests go directly from the user's browser to the address the Customer configured; they do not pass through RDC's servers. A request contains what is needed for the task, such as the user's question and the data of the work item concerned.
- A personal token is kept in user-scoped extension data and only the user can read it. Tokens are never written to logs, work items, Discussion or Git.
- How the provider processes the data is governed by the Customer's agreement with that provider.

## 5. Other third-party connections

If the Customer connects the Product to systems such as a test platform, systems of record (for example ITSM, CMDB, GRC) or a directory service, the data is sent directly to the address the Customer configured. Processing in those systems is governed by the Customer's agreements with them.

## 6. Retention

- Data in the Customer's organization stays in Azure DevOps until the Customer deletes it or removes the extension and its data.
- Information sent to RDC with a license application is kept for the duration of the license relationship and for the period required by applicable law, and is then deleted or anonymized.

## 7. Data protection and responsibility

Product data is hosted on Microsoft's systems when Azure DevOps Services is used, and on servers the Customer manages when Azure DevOps Server is used. Backing up, retaining, deleting and protecting data is the responsibility of the Customer and of the hosting provider; RDC accepts no responsibility for these matters or for security breaches in these systems. Details are in the "Disclaimer of responsibility" section of the end user license agreement.

## 8. Your rights

Under the Turkish Personal Data Protection Law (KVKK) and, where applicable, the GDPR you have the rights of access, rectification, erasure, restriction of processing, objection and data portability. Send requests to it4it@rdc.com.tr. For data in the Customer's Azure DevOps organization, contact your organization's administrator.

## 9. Changes

RDC may update this notice. The current version is published with the Product and on the Marketplace page.
