# IT-Stream: başlarken

Sürüm 1.0 · 9 Kasım 2026

IT-Stream, IT4IT™ 3.0.1 standardını temel alan bir Azure DevOps eklentisidir. Bu sayfa eklentiyi kurup ilk projenizi çalıştırmanız için gereken adımları anlatır. Ayrıntılı belgeler ürünün içindedir (bkz. [Öğrenme kaynakları](LEARN.md)).

## Ön koşullar

- Bir Azure DevOps Services kurumu.
- Kurumda **Project Collection Administrators** üyeliği: eklentiyi kurmak ve süreci özelleştirmek için gerekir.
- Devralınmış (inherited) süreç kullanan ya da yeni bir devralınmış sürece taşınabilecek bir proje.

## 1. Eklentiyi kurun

1. Marketplace'te IT-Stream sayfasında **Get it free** ya da **Get** düğmesini seçin ve kurumunuzu seçin.
2. Eklentinin istediği izinleri onaylayın. Her işlem, işlemi yapan kullanıcının kendi Azure DevOps yetkisiyle yapılır.

## 2. Süreci kurun

1. **Organizasyon ayarları › IT-Stream süreç kurulumu** sayfasını açın.
2. Hedef süreci seçin ya da yeni bir devralınmış süreç oluşturun.
3. **Planı çıkar** ile yapılacak değişiklikleri görün: iş öğesi tipleri, alanlar, durumlar, form sayfaları ve backlog düzeyleri.
4. Planı inceledikten sonra **Uygula**'yı seçin. Kurulum yeniden çalıştırılabilir; yalnız eksik ya da değişen öğeler uygulanır.

## 3. Projeyi taşıyın

**Organizasyon ayarları › Process** altında projenizi kurulan sürece taşıyın. Mevcut iş öğeleriniz korunur.

## 4. Çalışmaya başlayın

1. Proje sol menüsündeki **IT-Stream** grubundan **Genel Bakış** sayfasını açın. **Eğitim** sayfasındaki rehberli turlar ilk adımları rolünüze göre gösterir.
2. Denemek için **IT-Stream süreç kurulumu › Demo verisi › Ürünle gelen veri kümeleri** listesinden bir örnek kurum yükleyebilirsiniz. Kümeler kurgusaldır.
3. İş öğesi formunda durum değiştirdiğinizde kapı denetimi eksik alanları ve karar verecek rolü gösterir.

## 5. Lisans

Bütün Enterprise modüllerini 30 gün boyunca anahtarsız deneyebilirsiniz. Lisans anahtarını ya da ücretsiz lisans başvurusunu **Ayarlar › Lisans** bölümünden yönetin.

## Yeni sürümler

Yeni izin isteyen bir sürüm, kurum yöneticisi **Organizasyon ayarları › Extensions** altında yeniden onaylayana kadar güncellenmez. Sürüm notunun "Kullanıcının yapacakları" bölümü yeniden onayın ya da süreç kurulumunun yeniden uygulanmasının gerekip gerekmediğini yazar.

## Yardım

Destek: [it4it@rdc.com.tr](mailto:it4it@rdc.com.tr) ve Marketplace'teki Soru ve Cevap bölümü. Ayrıntılar: [Destek politikası](SUPPORT.md).

---

# IT-Stream: getting started

Version 1.0 · 9 November 2026

IT-Stream is an Azure DevOps extension based on the IT4IT™ 3.0.1 standard. This page lists the steps to install it and run your first project. Detailed documentation ships inside the product (see [Learning resources](LEARN.md)).

## Prerequisites

- An Azure DevOps Services organization.
- Membership in **Project Collection Administrators**, required to install the extension and customize the process.
- A project that uses an inherited process or can be moved to a new inherited process.

## 1. Install the extension

1. On the IT-Stream Marketplace page select **Get it free** or **Get** and choose your organization.
2. Approve the requested permissions. Every operation runs with the Azure DevOps permissions of the user who performs it.

## 2. Set up the process

1. Open **Organization settings › IT-Stream süreç kurulumu** (process setup).
2. Select the target process or create a new inherited process.
3. Use **Planı çıkar** (generate plan) to review the changes: work item types, fields, states, form pages and backlog levels.
4. After reviewing the plan select **Uygula** (apply). Setup can be re-run; only missing or changed items are applied.

## 3. Move your project

Under **Organization settings › Process**, move your project to the new process. Existing work items are kept.

## 4. Start working

1. Open **IT-Stream › Genel Bakış** (overview) in the project menu. The guided tours on the **Eğitim** (training) page show the first steps for your role.
2. To try the product, load a sample organization from **IT-Stream süreç kurulumu › Demo verisi › Ürünle gelen veri kümeleri**. The data sets are fictional.
3. When you change a state on the work item form, the gate check lists missing fields and the deciding role.

## 5. License

All Enterprise modules can be tried for 30 days without a key. Manage the license key or apply for a free license under **Ayarlar › Lisans** (settings › license).

## New versions

A version that requests new permissions is not updated until an organization administrator approves it again under **Organization settings › Extensions**. The "Kullanıcının yapacakları" (user actions) section of the release notes tells you whether re-approval or re-applying the process setup is needed.

## Help

Support: [it4it@rdc.com.tr](mailto:it4it@rdc.com.tr) and the Marketplace Q&A. Details: [Support policy](SUPPORT.md).

IT4IT™, ArchiMate® and TOGAF® are trademarks of The Open Group. IT-Stream is not endorsed or certified by The Open Group.
