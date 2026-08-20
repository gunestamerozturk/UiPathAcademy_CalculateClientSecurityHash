# Calculate Client Security Hash - UiPath REFramework

## 📌 Proje Özeti
Bu proje, **UiPath Academy - Automation Developer Professional Training** eğitimi kapsamında geliştirilmiştir. ACME System 1 web uygulaması ve SHA-1 şifreleme aracı kullanılarak müşteri verileri için güvenli hash (şifre) hesaplama sürecini otomatize etmek amacıyla **Robotic Enterprise Framework (REFramework)** mimarisi kullanılmıştır.

## ⚙️ Süreç Akışı
1. **Başlatma (Initialization):** ACME System 1 uygulamasına giriş yapılır ve SHA-1 online aracı açılır.
   - İş Öğeleri (Work Items) tablosu çekilir ve sadece türü **WI5**, durumu **Open** olan öğeler filtrelenir.
   - Filtrelenen öğeler **Orchestrator**'da kuyruğa eklenir.
2. **Veri Alma (Get Transaction Data):** Orchestrator'daki kuyruktaki veriler sırasıyla Process'e aktarılır.
3. **İşlem (Process Transaction):**
   - Kuyruktaki her WI5 öğesi için Müşteri Detayları (Client Details) sayfasına gidilir.
   - `Client ID`, `Client Name` ve `Client Country` bilgileri ayıklanır.
   - Ayıklanan veriler tek bir metin halinde birleştirilir: `ClientID-ClientName-ClientCountry`.
   - Bu metin, güvenli hash değerini almak için SHA-1 online aracına girilir.
   - ACME System 1'deki ilgili İş Öğesi, oluşturulan hash değeriyle güncellenir ve durumu **Completed** (Tamamlandı) olarak değiştirilir.
4. **Bitiş (End Process):** Güvenli bir şekilde sistemden çıkış yapılır ve tüm web uygulamaları kapatılır.

## 🛠️ Kullanılan Teknolojiler ve Yetkinlikler
- **Robotic Enterprise Framework** 
- **Web Otomasyonu ve Veri Kazıma**
- **Metin İşleme (String Manipulation) ve Veri Ayıklama**
- **UiPath Orchestrator** (Asset ve Credential Yönetimi)
- **Hata Yönetimi (Exception Handling) ve Sistem Loglama**

## 🚀 Kurulum ve Çalıştırma
1. Bu depoyu (repository) bilgisayarınıza klonlayın.
2. [ACME System 1](https://acme-test.uipath.com/) üzerinde aktif bir hesabınız olduğundan emin olun.
3. UiPath Orchestrator'da aşağıdaki Asset'leri oluşturun ve yapılandırın:
   - `AcmeUser`: (Credential) ACME System 1 giriş bilgileriniz.
   - `System1_URL`: (Text) `https://acme-test.uipath.com/`
   - `SHA1_Online_URL`: (Text) `https://emn178.github.io/online-tools/sha1.html`
4. Projeyi UiPath Studio'da açın ve `Main.xaml` dosyasını çalıştırın.
