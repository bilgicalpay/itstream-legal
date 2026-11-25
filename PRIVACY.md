# IT-Stream gizlilik bildirimi

Sürüm 2.3 · 24 Kasım 2026 · Sürüm 2.2'nin (23 Kasım 2026) yerini alır

Bu bildirim, Azure DevOps eklentisi "IT-Stream" ile bağımsız IT-Stream Sihirbazının (bundan sonra "Ürün") hangi verileri nerede sakladığını, RDC Partner'a (bundan sonra "RDC") neleri gönderdiğini ve RDC'nin lisans sahibi bilgisini nasıl işlediğini açıklar. Bildirim, IT-Stream Son Kullanıcı Lisans Sözleşmesinin (EULA.md) 5. ve 9. bölümlerini ayrıntılandırır.

## 1. Veri sorumlusu

- Müşterinin Azure DevOps kurumunda oluşturduğu ve işlediği verilerin, kabul kaydı dahil, sorumlusu Müşteridir. RDC bu verilere erişmez.
- Lisans sahibi bilgisinin, kullanım bildiriminin, lisans başvurusunun ve RDC ile yazışmalarda iletilen bilgilerin sorumlusu RDC Partner'dır. İletişim: it4it@rdc.com.tr

## 2. Müşterinin Azure DevOps kurumunda saklanan veriler

Ürün çalışması için gereken verileri Müşterinin kendi Azure DevOps kurumunda saklar ve RDC'nin sunucularına aktarmaz:

- İş öğeleri, alanlar, bağlantılar ve Discussion yorumları (Azure DevOps'un kendi deposu).
- Ayarlar, ArchiMate modeli, denetim kayıtları, maliyet kataloğu ve benzeri belgeler (Azure DevOps eklenti verisi deposu; kurum, proje ya da kullanıcı kapsamında).
- Lisans belgesi: lisans anahtarı, lisans sunucusu adresi, önceki anahtarların parmak izleri ve kullanım bildiriminin son gönderim kaydı (zaman, dönem, sonuç, art arda başarısız deneme sayısı).
- Etkin kullanıcı sayımı: her kullanıcı için tuzlu SHA-256 özetinden üretilen takma kimlik ve modüllerin son kullanım günleri. Ad, e-posta ya da açık kullanıcı kimliği yazılmaz.
- Kabul kaydı: 5. bölümde açıklanır.
- Bağlantıların gizli değerleri (parola, token) Azure Pipelines Library değişken gruplarında gizli değer olarak tutulur; Ürün bunları eklenti verisine yazmaz.

Bağımsız sihirbaz verileri yalnız kullanıcının tarayıcısında (tarayıcı deposu) ya da kullanıcının indirdiği dosyalarda tutar; RDC'ye kullanım bildirimi ya da başka veri iletmez.

## 3. Lisans denetimi ve RDC'ye gönderilen veriler

- **Doğrulama.** Lisans anahtarı Ürünün içinde, RDC'nin açık anahtarıyla doğrulanır. Doğrulama çevrim dışıdır; doğrulama için RDC'ye istek gönderilmez.
- **Zorunlu kullanım bildirimi.** Lisans yönetimi için gereklidir ve kapatılamaz. Doğrulanmış lisans kimliği olan her kurumda Ürün, RDC'nin lisans sunucusuna (varsayılan https://gotime.higgscloud.com) haftada en çok bir kez kullanım bildirimi gönderir: son denemeden 7 gün sonra IT-Stream'i açan ilk oturum gönderir. Lisans kaydedilmediyse ya da anahtar doğrulanamıyorsa bildirim gönderilmez.
- Kullanım bildirimi yalnız şu alanları taşır:

| Alan | Açıklama |
| :--- | :--- |
| Ürün kimliği | Ürünün lisans kimliği (`it4it-surec`) |
| Lisans kimliği | Lisans anahtarındaki kimlik |
| Kurum ya da sunucu adı | Azure DevOps Services kurumunun ya da Azure DevOps Server sunucusunun adı |
| Son 30 günün etkin kullanıcı sayısı | Tek bir sayı |
| Lisanstaki modüllerin etkin kullanıcı sayıları | Yalnız lisanstaki modüller; lisansta olmayan modülün sayısı gönderilmez |
| Eklenti sürümü | Ör. 0.9.210 |
| Dönem (ISO hafta) | Ör. 2026-W46 |

- **Etkin kullanıcılar.** Kullanım bildirimi etkin kullanıcıların adını, e-posta adresini, kullanıcı kimliğini ya da takma kimliğini taşımaz; proje adı ve iş öğesi verisi de bildirimde yer almaz. Bildirimdeki lisans kimliği, bildirimi RDC'deki lisans kaydına bağlar. Lisans kaydı lisans sahibi bilgisini içerdiği için RDC bildirimi lisans sahibiyle ilişkilendirebilir (4. bölüm).
- **Kapalı ağ.** Lisans sunucusuna erişilemezse (ör. internete kapalı Azure DevOps Server) gönderim başarısız olur; hata sessizdir, hiçbir sayfa ya da özellik kapanmaz ve yeniden deneme bir hafta sonradır. Art arda 4 deneme başarısız olursa kurum yöneticilerine bilgi şeridi çıkar. RDC yazılı olarak isterse kurum yöneticisi Ayarlar › Lisans'taki sayım özetini RDC'ye kendisi iletir; özet bildirimle aynı alanları taşır.
- **Deneme lisansı.** Kurum yöneticisi Ürünün içinden deneme lisansı istediğinde Ürün, isteği göndermeden önce aşağıdaki bilgilerin tam listesini ve değerlerini gösterir; yönetici onaylarsa bilgiler lisans sunucusuna gönderilir. Okunamayan bilgi gönderilmez ve istek o bilgi olmadan gider; örneğin eklentinin kurum kullanıcılarını okuma izni onaylanmadıysa kurumdaki kullanıcı sayısı gönderilmez. RDC bu bilgileri lisans boyutlandırma, fiyat teklifi ve kurulum desteği için kullanır ve lisans kaydında lisans sahibi bilgisiyle birlikte saklar (4. ve 9. bölüm).

| İstek alanı | Açıklama |
| :--- | :--- |
| Kurum ya da sunucu adı | Azure DevOps Services kurumunun ya da Azure DevOps Server sunucusunun adı |
| Eklenti sürümü | Ör. 0.9.254 |
| İsteği yapan kişinin görünen adı | Azure DevOps oturumundaki ad |
| İsteği yapan kişinin e-posta adresi | Oturum adı e-posta biçimindeyse |
| İsteği yapan kişinin Azure DevOps kullanıcı kimliği | Tek bir kimlik (GUID) |
| Kurumdaki kullanıcı sayısı | Tek bir sayı; hizmet hesapları sayılmaz |
| Kurumdaki proje sayısı | Tek bir sayı; proje adları gönderilmez |
| Son 30 günün etkin kullanıcı sayısı | Tek bir sayı; etkin kullanıcıların kimliği gönderilmez |

- **Ücretsiz lisans başvurusu.** Başvuru formu lisans sunucusunda yeni sekmede açılır ve formun kurum adı alanı önceden doldurulur. Formda yazılan ad soyad, görev ve e-posta adresi RDC'ye ulaşır; başvuru onaylanırsa bu bilgiler lisans sahibi bilgisi olur.

## 4. Lisans sahibi bilgisi

Lisans sahibi, Müşteri adına lisansı isteyen, lisans başvurusu yapan, lisansı satın alan ya da lisans anahtarını alıp Ürüne yükleyen ve RDC'nin lisans kaydında Müşterinin ilgili kişisi olarak yer alan kişidir.

- **Bilgiler.** Lisans kaydında lisans sahibinin adı soyadı, e-posta adresi, görevi, verildiyse telefon numarası ve Müşterinin adı saklanır. İsteğin ya da yüklemenin yapıldığı kanala göre kişinin Azure DevOps kullanıcı adı ya da kimliği de bunlara eklenebilir. Deneme lisansı eklentiden istendiyse kayıtta kişinin Azure DevOps kullanıcı kimliği ile kurumdaki kullanıcı, proje ve etkin kullanıcı sayıları da bulunur (3. bölüm).
- **Kanallar.** Bu bilgiler RDC'ye şu yollarla ulaşır: ücretsiz lisans başvuru formu; lisans siparişi, teklif ve fatura yazışmaları; eklentiden alınan deneme lisansı ve RDC'ye iletilen lisans istekleri; lisans anahtarının lisans sahibine iletilmesi ve Ürüne yüklenmesi; destek ve sayım özeti yazışmaları; Azure DevOps Marketplace'in Microsoft'un koşullarıyla yayıncıya sağladığı kurulum bilgileri.
- **Kullanım.** RDC lisans sahibine lisansla ilgili bildirimleri (bitiş, yenileme, koltuk ve kullanım bildirimi uyarıları), faturaları ve destek yanıtlarını gönderir. Kullanım bildirimleri lisans kimliğiyle lisans kaydına bağlıdır.
- **Aktarım.** Lisans sahibi bilgisi RDC'nin lisans sunucusunda ve bildirimlerin gönderildiği e-posta hizmetinde işlenir; pazarlama amacıyla üçüncü kişilere aktarılmaz.
- **Değişiklik.** Lisans sahibi değişirse (ör. kişi görevinden ayrılırsa) Müşteri yeni kişiyi it4it@rdc.com.tr adresine bildirir. Önceki kişinin bilgisi 9. bölümdeki sürelerle saklanır.

## 5. Kabul kaydı

- Ürün, lisans sözleşmesinin yürürlükteki sürümünü ve kullanım bildirimini her kullanıcıya, sözleşme sürümü başına bir kez, ilk açılışta bildirir. Kullanıcının bildirimi gördüğü, kullanıcı kapsamlı eklenti verisine görülen sözleşme sürümüyle yazılır.
- Kurum kapsamındaki eklenti verisinde (`it4it-lisans-kabul` koleksiyonu) sözleşme sürümü başına tek bir kabul kaydı tutulur: sözleşme sürümü, zaman, bildirimi kurumda ilk gören kişinin Azure DevOps kimliği ve adı ve bildirimi gören kişi sayısı.
- Kabul kaydı Müşterinin kurumunda saklanır; RDC'ye gönderilmez. Kayıttaki kişi adı ve kimliği Müşterinin işlediği kişisel veridir.

## 6. İşleme amaçları ve hukuki dayanak

| Veri | Amaç | Dayanak |
| :--- | :--- | :--- |
| Kullanım bildirimi | Lisans kapsamına uyumun izlenmesi, faturalama, destek ve sürüm uyumluluğu | Lisans sözleşmesinin kurulması ve ifası; RDC'nin lisans haklarını korumadaki meşru menfaati |
| Lisans sahibi bilgisi (ad soyad, e-posta adresi, görev, telefon, Müşterinin adı) | Lisans vermek ve yönetmek, faturalama, lisans bildirimleri, destek ve Müşteriyle iletişim | Lisans sözleşmesinin kurulması ve ifası; faturalama ve muhasebe kayıtlarında RDC'nin hukuki yükümlülüğü; RDC'nin lisans haklarını korumadaki meşru menfaati |
| Ücretsiz lisans başvurusundaki bilgiler | Başvurunun değerlendirilmesi ve sonucun bildirilmesi | Lisans sözleşmesinin kurulması |
| Deneme lisansı isteğindeki kurum ölçüleri (kurumdaki kullanıcı ve proje sayısı, etkin kullanıcı sayısı) | Lisans boyutlandırma, fiyat teklifi ve kurulum desteği | Lisans sözleşmesinin kurulması ve ifası; RDC'nin lisans haklarını korumadaki meşru menfaati |
| Kabul kaydı | Sözleşmenin bildirildiğinin Müşterinin kendi kurumunda kanıtlanması | Müşterinin dayanağı; RDC bu kaydı işlemez |

KVKK ve GDPR bakımından tablodaki işlemeler sözleşmenin kurulması ve ifası, hukuki yükümlülük ve meşru menfaat sebeplerine dayanır; bu işlemeler için ayrıca açık rıza istenmez. RDC bu verileri pazarlama amacıyla üçüncü kişilere aktarmaz.

## 7. Yapay zekâ özellikleri

- Yapay zekâ özellikleri yalnız Müşteri bir sağlayıcı (ör. Azure OpenAI, OpenAI uyumlu servis, Anthropic) yapılandırdığında çalışır.
- İstekler kullanıcının tarayıcısından doğrudan Müşterinin yapılandırdığı adrese gider; RDC'nin sunucularından geçmez. İstekte, kullanıcının sorusu ve ilgili iş öğesinin verisi gibi işi yapmak için gereken içerik bulunur.
- Kişisel token kullanıcı kapsamlı eklenti verisinde tutulur ve yalnız kullanıcının kendisi okur. Token günlüğe, iş öğesine, Discussion'a ya da Git'e yazılmaz.
- Sağlayıcının veriyi nasıl işlediği Müşterinin o sağlayıcıyla yaptığı sözleşmeye tabidir.

## 8. Diğer üçüncü taraf bağlantıları

Müşteri Ürünü test platformu, kayıt sistemleri (ör. ITSM, CMDB, GRC) ya da dizin hizmeti gibi sistemlere bağlarsa veri, Müşterinin yapılandırdığı adrese doğrudan gönderilir. Bu sistemlerdeki işleme, Müşterinin o sistemlerle yaptığı sözleşmelere tabidir.

## 9. Saklama süresi

- Müşterinin kurumundaki veriler, kabul kaydı dahil, Müşteri silene ya da eklentiyi ve verisini kaldırana kadar Azure DevOps'ta kalır.
- Kullanım bildirimleri lisans ilişkisi süresince ve yürürlükteki mevzuatın öngördüğü süre boyunca saklanır.
- Lisans sahibi bilgisi lisans süresince ve lisans sona erdikten sonra 1 yıl saklanır; fatura ve muhasebe kayıtlarına giren bilgiler yürürlükteki mevzuatın öngördüğü süre boyunca saklanır. Süre dolunca bilgiler silinir ya da anonim hâle getirilir.
- Deneme lisansı isteğindeki bilgiler lisans kaydında lisans sahibi bilgisiyle aynı süre boyunca saklanır.
- Reddedilen ücretsiz lisans başvuruları karar tarihinden 180 gün sonra silinir.

## 10. Verinin korunması ve sorumluluk

Ürünün verisi Azure DevOps Services kullanıldığında Microsoft'un sistemlerinde, Azure DevOps Server kullanıldığında Müşterinin kendi yönettiği sunucularda barındırılır. Verinin yedeklenmesi, saklanması, silinmesi ve korunması Müşterinin ve barındırma hizmetini sağlayanın sorumluluğundadır; RDC bu konularda ve bu sistemlerde meydana gelen güvenlik ihlallerinde sorumluluk kabul etmez. Ayrıntılar son kullanıcı lisans sözleşmesinin 12. bölümündedir (Sorumluluğun sınırlandırılması).

## 11. Haklarınız

KVKK ve uygulanabildiği ölçüde GDPR kapsamında kişisel verilerinize erişme, düzeltme, silme, işlemeyi kısıtlama, itiraz etme ve veri taşınabilirliği haklarınız vardır. Taleplerinizi it4it@rdc.com.tr adresine iletin. Lisans sahibi olarak kayıtlı bilgileriniz için de aynı adrese başvurabilirsiniz. Müşterinin Azure DevOps kurumundaki veriler için, kabul kaydı dahil, kurumunuzun yöneticisine başvurun.

## 12. Değişiklikler ve sürüm geçmişi

RDC bu bildirimi güncelleyebilir. Güncel sürüm Ürünle ve Marketplace sayfasındaki gizlilik bağlantısıyla yayımlanır. Kullanım bildiriminin alanları artarsa bildirim ve lisans sözleşmesi birlikte güncellenir.

| Sürüm | Tarih | Değişiklik |
| :--- | :--- | :--- |
| 1.0 | 6 Kasım 2026 | İlk yayın |
| 2.0 | 19 Kasım 2026 | Zorunlu kullanım bildirimi ve alanları; kabul kaydı; işleme amaçları ve dayanak; saklama süreleri |
| 2.2 | 23 Kasım 2026 | Sürüm numarası lisans sözleşmesiyle eşitlendi (gizlilik bildiriminin 2.1 sürümü yoktur). Lisans sahibi bilgisi (4. bölüm): bilgiler, RDC'ye ulaştığı yollar, kullanım, aktarım ve saklama süresi; kullanım bildirimiyle ilgili madde etkin kullanıcılarla sınırlandı ve lisans kaydıyla bağı yazıldı; ücretsiz lisans başvurusu ve reddedilen başvurunun saklama süresi |
| 2.3 | 24 Kasım 2026 | Deneme lisansı isteğinin taşıdığı bilgiler (3. bölüm): isteği yapan kişinin adı, e-posta adresi ve Azure DevOps kullanıcı kimliği, kurumdaki kullanıcı ve proje sayısı, etkin kullanıcı sayısı; bilgilerin istekten önce gösterilmesi, amacı (lisans boyutlandırma, fiyat teklifi, kurulum desteği), işleme dayanağı (6. bölüm) ve saklama süresi (9. bölüm) |

---

# IT-Stream privacy notice

Version 2.3 · 24 November 2026 · Replaces version 2.2 (23 November 2026)

This notice explains which data the Azure DevOps extension "IT-Stream" and the standalone IT-Stream Wizard ("Product") store and where, what they send to RDC Partner ("RDC"), and how RDC processes license owner details. It details sections 5 and 9 of the IT-Stream End User License Agreement (EULA.md).

## 1. Data controller

- The Customer is the controller of the data it creates and processes in its Azure DevOps organization, including the acceptance record. RDC has no access to this data.
- RDC Partner is the controller of license owner details, usage reports, license applications and information sent in correspondence with RDC. Contact: it4it@rdc.com.tr

## 2. Data stored in the Customer's Azure DevOps organization

The Product stores the data it needs in the Customer's own Azure DevOps organization and does not transfer it to RDC's servers:

- Work items, fields, links and Discussion comments (Azure DevOps' own store).
- Settings, the ArchiMate model, audit records, the cost catalog and similar documents (the Azure DevOps extension data store; at organization, project or user scope).
- The license document: the license key, the license server address, fingerprints of previous keys and the last usage report record (time, period, result, number of consecutive failed attempts).
- Active user counting: for each user, a pseudonymous identifier derived from a salted SHA-256 hash and the last days the modules were used. No name, e-mail address or plain user ID is written.
- The acceptance record: described in section 5.
- Secret values of connections (passwords, tokens) are kept as secret values in Azure Pipelines Library variable groups; the Product does not write them to extension data.

The standalone wizard keeps data only in the user's browser (browser storage) or in files the user downloads; it sends RDC no usage report or other data.

## 3. License check and data sent to RDC

- **Verification.** The license key is verified inside the Product with RDC's public key. Verification is offline; no request is sent to RDC for verification.
- **Mandatory usage report.** It is required for license management and cannot be turned off. In every organization with a verified license ID the Product sends a usage report to RDC's license server (by default https://gotime.higgscloud.com) at most once a week: the first session that opens IT-Stream 7 days after the last attempt sends it. No report is sent if no license is saved or the key cannot be verified.
- The usage report carries only these fields:

| Field | Description |
| :--- | :--- |
| Product ID | The Product's license ID (`it4it-surec`) |
| License ID | The ID in the license key |
| Organization or server name | The name of the Azure DevOps Services organization or Azure DevOps Server host |
| Active users in the last 30 days | A single number |
| Active users of the licensed modules | Licensed modules only; counts of modules not in the license are not sent |
| Extension version | For example 0.9.210 |
| Period (ISO week) | For example 2026-W46 |

- **Active users.** The usage report does not carry the names, e-mail addresses, user IDs or pseudonymous IDs of active users; nor does it carry project names or work item data. The license ID in the report links it to RDC's license record. Because the license record contains the license owner details, RDC can associate the report with the license owner (section 4).
- **Closed networks.** If the license server cannot be reached (for example an Azure DevOps Server without internet access), the transmission fails; the error is silent, no page or feature closes and the next attempt is a week later. After 4 failed attempts in a row an information banner is shown to organization administrators. If RDC asks in writing, the organization administrator sends RDC the count summary from Settings › License (Ayarlar › Lisans); the summary carries the same fields as the report.
- **Trial licenses.** When an organization administrator requests a trial license from inside the Product, the Product shows the full list of the details below with their values before sending the request; if the administrator confirms, the details are sent to the license server. A detail that cannot be read is not sent and the request goes without it; for example, if the extension's permission to read the organization's users has not been approved, the number of users in the organization is not sent. RDC uses these details for license sizing, price quotes and installation support, and keeps them in the license record together with the license owner details (sections 4 and 9).

| Request field | Description |
| :--- | :--- |
| Organization or server name | The name of the Azure DevOps Services organization or Azure DevOps Server host |
| Extension version | For example 0.9.254 |
| Display name of the person making the request | The name in the Azure DevOps session |
| E-mail address of the person making the request | If the sign-in name is an e-mail address |
| Azure DevOps user ID of the person making the request | A single ID (GUID) |
| Number of users in the organization | A single number; service accounts are not counted |
| Number of projects in the organization | A single number; project names are not sent |
| Active users in the last 30 days | A single number; the identities of active users are not sent |

- **Free license applications.** The application form opens on the license server in a new tab and its organization name field is pre-filled. The full name, job title and e-mail address entered in the form reach RDC; if the application is approved, they become the license owner details.

## 4. License owner details

The license owner is the person who, on the Customer's behalf, requests a license, applies for a license, purchases a license, or receives the license key and enters it into the Product, and who is recorded in RDC's license record as the Customer's contact person.

- **Details.** The license record holds the license owner's full name, e-mail address, job title, telephone number if given, and the Customer's name. Depending on the channel used for the request or the key entry, the person's Azure DevOps user name or ID may be added to them. If the trial license was requested from the extension, the record also holds the person's Azure DevOps user ID and the number of users, projects and active users in the organization (section 3).
- **Channels.** These details reach RDC through: the free license application form; license orders, quotes and invoicing correspondence; trial licenses obtained from the extension and license requests sent to RDC; delivery of the license key to the license owner and its entry into the Product; support and count summary correspondence; installation information that the Azure DevOps Marketplace provides to the publisher under Microsoft's terms.
- **Use.** RDC sends the license owner license notices (expiry, renewal, seat and usage report warnings), invoices and support replies. Usage reports are linked to the license record by the license ID.
- **Transfers.** License owner details are processed on RDC's license server and in the e-mail service used to send notices; they are not passed to third parties for marketing.
- **Changes.** If the license owner changes (for example the person leaves the role), the Customer notifies it4it@rdc.com.tr of the new person. The previous person's details are kept for the periods in section 9.

## 5. Acceptance record

- On first use the Product shows every user, once per agreement version, a notice of the current version of the license agreement and of the usage report. That the user saw the notice is written to user-scoped extension data with the agreement version seen.
- One acceptance record per agreement version is kept in organization-scoped extension data (the `it4it-lisans-kabul` collection): the agreement version, the time, the Azure DevOps ID and name of the first person in the organization who saw the notice, and the number of people who saw it.
- The acceptance record is stored in the Customer's organization; it is not sent to RDC. The person's name and ID in the record are personal data processed by the Customer.

## 6. Purposes and legal basis of processing

| Data | Purpose | Basis |
| :--- | :--- | :--- |
| Usage report | Monitoring compliance with the license scope, invoicing, support and version compatibility | Formation and performance of the license agreement; RDC's legitimate interest in protecting its license rights |
| License owner details (full name, e-mail address, job title, telephone, Customer's name) | Issuing and managing licenses, invoicing, license notices, support and communicating with the Customer | Formation and performance of the license agreement; RDC's legal obligation for invoicing and accounting records; RDC's legitimate interest in protecting its license rights |
| Information in free license applications | Assessing the application and notifying the result | Formation of the license agreement |
| Organization measures in a trial license request (number of users and projects in the organization, number of active users) | License sizing, price quotes and installation support | Formation and performance of the license agreement; RDC's legitimate interest in protecting its license rights |
| Acceptance record | Evidence, in the Customer's own organization, that the agreement was notified | The Customer's basis; RDC does not process this record |

Under KVKK and the GDPR, the processing in the table relies on the formation and performance of a contract, legal obligation and legitimate interest; no separate explicit consent is requested for this processing. RDC does not pass this data to third parties for marketing.

## 7. AI features

- AI features work only when the Customer configures a provider (for example Azure OpenAI, an OpenAI-compatible service or Anthropic).
- Requests go directly from the user's browser to the address the Customer configured; they do not pass through RDC's servers. A request contains what is needed for the task, such as the user's question and the data of the work item concerned.
- A personal token is kept in user-scoped extension data and only the user can read it. Tokens are never written to logs, work items, Discussion or Git.
- How the provider processes the data is governed by the Customer's agreement with that provider.

## 8. Other third-party connections

If the Customer connects the Product to systems such as a test platform, systems of record (for example ITSM, CMDB, GRC) or a directory service, the data is sent directly to the address the Customer configured. Processing in those systems is governed by the Customer's agreements with them.

## 9. Retention

- Data in the Customer's organization, including the acceptance record, stays in Azure DevOps until the Customer deletes it or removes the extension and its data.
- Usage reports are kept for the duration of the license relationship and for the period required by applicable law.
- License owner details are kept for the term of the license and for 1 year after the license ends; information included in invoices and accounting records is kept for the period required by applicable law. When the period ends, the details are deleted or anonymized.
- The details in a trial license request are kept in the license record for the same period as the license owner details.
- Rejected free license applications are deleted 180 days after the decision.

## 10. Data protection and responsibility

Product data is hosted on Microsoft's systems when Azure DevOps Services is used, and on servers the Customer manages when Azure DevOps Server is used. Backing up, retaining, deleting and protecting data is the responsibility of the Customer and of the hosting provider; RDC accepts no responsibility for these matters or for security breaches in these systems. Details are in section 12 (Limitation of liability) of the end user license agreement.

## 11. Your rights

Under the Turkish Personal Data Protection Law (KVKK) and, where applicable, the GDPR you have the rights of access, rectification, erasure, restriction of processing, objection and data portability. Send requests to it4it@rdc.com.tr. You can also use this address for the details recorded about you as license owner. For data in the Customer's Azure DevOps organization, including the acceptance record, contact your organization's administrator.

## 12. Changes and version history

RDC may update this notice. The current version is published with the Product and at the privacy link on the Marketplace page. If fields are added to the usage report, this notice and the license agreement are updated together.

| Version | Date | Change |
| :--- | :--- | :--- |
| 1.0 | 6 November 2026 | First publication |
| 2.0 | 19 November 2026 | Mandatory usage report and its fields; acceptance record; purposes and legal basis; retention periods |
| 2.2 | 23 November 2026 | Version number aligned with the license agreement (there is no version 2.1 of this notice). License owner details (section 4): the details, how they reach RDC, use, transfers and retention; the usage report clause limited to active users and its link to the license record stated; free license applications and retention of rejected applications |
| 2.3 | 24 November 2026 | Details carried by the trial license request (section 3): the requesting person's name, e-mail address and Azure DevOps user ID, the number of users and projects in the organization, the number of active users; showing the details before the request, their purpose (license sizing, price quotes, installation support), legal basis (section 6) and retention (section 9) |
