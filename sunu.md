# Contract management and contract testing

## SUNU 01

### İçerik
- **Ana başlık:** Dijital Dönüşümde Emniyet Kemeri
- **Alt başlık:** Contract Management - Contract Testing
- **En Alt:**
  Ali Osman ALATAŞ
  Lider Uzman
  Orta Katman ve Framework Çözümleri Müdürlüğü

### Konuşma metni
Merhabalar. Ben Ali Osman Alataş. Orta Katman ve Framework Çözümleri Müdürlüğü (OKF) bünyesinde Lider Uzman olarak görev yapıyorum.

Bugün sizlerle **Contract Management** ve **Contract Testing** üzerine konuşmak için bir aradayız. Konuyu bir sunumla görselleştirdim; yaklaşık **12 dakika** sürecek.

Bankacılık sistemlerinde çok kritik ama çoğu zaman görünmeyen bir riske odaklanacağız. Bu risk aslında her gün yaşanıyor; çoğu zaman fark etmeden üzerinden geçiyoruz.
Bu sunumda hem bu riski netleştireceğim hem de onu **sistematik** bir şekilde nasıl yöneteceğimizi anlatacağım.

### Yönetici bu anda ne düşünür
"Emniyet kemeri metaforu ilginç. Dinleyelim."

### Olası soru
Yok. Henüz değil.

### Süre
15 saniye. Hemen geçin.

---

## SUNU 02

### İçerik
- **Başlık:** Görünmez Risk
- Bankacılık sistemleri onlarca servis üzerinden birbirine bağlıdır
- Her servis değiştiğinde, diğer servislerin çalışıp çalışmadığı bilinmez
- Entegrasyon kırılmaları genellikle üretim ortamında fark edilir
- Bu kırılmaların büyük çoğunluğu **API arayüz uyumsuzluklarından** kaynaklanır

### Konuşma metni
Bankacılık sistemleri artık tek parça değil. Onlarca, bazen yüzlerce servis birbiriyle konuşuyor. Ödeme servisi kredi servisine soruyor, kredi servisi müşteri servisine, müşteri servisi kimlik doğrulama servisine soruyor.

Bir ekip kendi servisini değiştirdiğinde, bu değişikliğin diğer servisleri kırıp kırmadığını çoğu zaman bilmiyor. Sormak da istemiyor çünkü bu çok zaman alıyor. Ve en kötüsü: kırılmalar çoğunlukla üretim ortamında—müşteri karşısında—ortaya çıkıyor.

Bu bir yazılım hatası değil; bu bir **görünmez risk**. Ve bu risk her gün büyüyor.

### Yönetici bu anda ne düşünür
"Bunu biz de yaşadık. Geçen çeyrekte bir entegrasyon sorunu ciddi etkilere yol açmıştı."

### Olası soru
Bu tür kırılmaların sıklığı nedir, ölçüyor muyuz?

### Süre
45 saniye.

---

## SUNU 03

### İçerik
- **Başlık:** Riskin Maliyeti
- Her entegrasyon kırılması: ortalama **4–8 saat** tespit + düzeltme süresi
- Üretimde yaşanan her olay: müşteri deneyimi kaybı, itibar riski
- Kırılmayı bulan ekip değil, **etkisi altında kalan ekip** fark eder
- Düzeltme maliyeti, erken tespite göre **10 kat** daha yüksek
- Sigortalı araç örneği: kaza olmadan önce emniyet kemeri takar mısınız?

### Konuşma metni
Peki bu görünmez riskin somut bedeli ne?

Bir entegrasyon kırılmasını tespit edip düzeltmek ortalama 4 ila 8 saat sürüyor. Bu süre yalnızca yazılım geliştirme değil; analiz, iletişim, test ve dağıtım süreçlerini de kapsıyor. Üretimde yaşandığında ise müşteri bunu hissediyor.

Daha da kritik olan şu: bu kırılmayı yaratan ekip değil, etkilenen ekip fark ediyor. Bu da çözümü daha da uzatıyor. Yazılım kalitesi alanındaki sektör araştırmaları gösteriyor ki üretimde fark edilen bir hatayı düzeltmek, geliştirme sürecinde fark edilene göre **ortalama 10 kat daha maliyetli** — IBM Systems Sciences Institute başta olmak üzere pek çok çalışma bu oranı teyit ediyor.

Emniyet kemerini kaza olduktan sonra takmaya çalışmak gibi.

### Yönetici bu anda ne düşünür
"10 kat maliyet farkı rakamı dikkat çekici. Kaynağı var mı?"

### Olası soru
Bu maliyeti bankamız özelinde ölçtük mü, ya da ölçebilir miyiz?

### Süre
50 saniye.

---

## SUNU 04

### İçerik
- **Başlık:** Sözleşme (Arayüz Anlaşması) Nedir?
- İki servis arasındaki **yazılı anlaşma**: "Sen benden şunu istersin, ben sana bunu dönerim"
- Alanlar, veri tipleri, zorunlu/isteğe bağlı parametreler
- Hata senaryoları ve beklenen yanıtlar
- Sözleşme = **ortak dil**; taraflar değişse bile dil sabit kalır
- Sözleşmesiz entegrasyon = sözlü anlaşma

### Konuşma metni
Peki çözüm nerede başlıyor? Sözleşmeden.

İki servis arasındaki sözleşme şunu söyler: "Sen benden şu alanları, şu formatta isteyeceksin; ben de sana şu yanıtı döneceğim." Alan adları, veri tipleri, hangi alanın zorunlu olduğu, hata durumlarında ne döneceği—bunların hepsi yazılı olarak tanımlanır.

Bunu bir dil olarak düşünün. İki kişi aynı dili konuştuğu sürece birbirini anlıyor. Ama sözleşme yoksa, bu ilişki sözlü bir anlaşmaya dönüşüyor—birisi "ben öyle dememiştim" diyor, diğeri "sen öyle demiştin" diyor.

Bankacılık dünyasında sözlü anlaşma kabul edilemez. Servisler arası ilişki de öyle.

### Yönetici bu anda ne düşünür
"Mantıklı. Ama bunu kim yazıyor, kim sahipleniyor?"

### Olası soru
Sözleşmeyi kim yazar ve kimin sorumluluğundadır?

### Süre
50 saniye.

---

## SUNU 05

### İçerik
- **Başlık:** Sözleşme Yönetimi (Contract Management) Nedir?
- Sözleşmelerin **merkezi olarak** tanımlanması, saklanması ve versiyonlanması
- Hangi sürüm, hangi ekip tarafından, ne zaman kullanılıyor?
- Değişiklik yönetimi: geriye dönük uyumluluk kontrolü
- Tüketici güdümlü yaklaşım: tüketen ekip ihtiyaçlarını tanımlar
- Sözleşme deposu (Contract Registry) = tek doğru kaynak

### Konuşma metni
Sözleşmeleri tanımlamak yetmiyor. Onları **yönetmek** gerekiyor.

Sözleşme Yönetimi; sözleşmelerin merkezi bir depoda tutulmasını, versiyonlanmasını ve değişikliklerin kontrollü biçimde yayılmasını sağlar.

Burada kritik bir kavram var: **tüketici güdümlü yaklaşım**. Yani sözleşmeyi üreten değil, tüketen ekip ihtiyaçlarını ortaya koyar. "Ben bu servisten şunu bekliyorum" der. Üretici bunu karşılayıp karşılamayacağını bilir.

Bu sayede bir servis değiştiğinde, hangi ekiplerin etkileneceği önceden görülür. Beklenmedik sürpriz olmaz. Değişiklik planlanabilir, koordineli şekilde yapılabilir.

Sözleşme deposu bu sürecin merkezidir—tek doğru kaynak.

### Yönetici bu anda ne düşünür
"Bu iyi bir fikir ama organizasyonel olarak uygulamak zor olabilir."

### Olası soru
Ekipler bu sözleşmeleri güncel tutmaya nasıl ikna edilecek?

### Süre
50 saniye.

---

## SUNU 06

### İçerik
- **Başlık:** Sözleşme Testi (Contract Testing) Nedir?
- Sözleşmenin **koda dönüşmesi**: elle kontrol değil, otomatik doğrulama
- Tüketici testi: "Servis benim beklediğim formatı döndürüyor mu?"
- Üretici testi: "Benim servisim tüm tüketicilerin sözleşmesini karşılıyor mu?"
- Sürekli entegrasyon (CI/CD) sürecine entegre edilir
- Kırılma **kod tabanında** yakalanır, üretimde değil

### Konuşma metni
Sözleşme yazıldı, depoya yüklendi. Güzel. Ama sözleşme gerçekten uygulanıyor mu?

İşte burada **Sözleşme Testi** devreye giriyor. Sözleşmeyi otomatik testlere dönüştürür.

İki yönlü çalışır. Tüketici tarafında: "Bu servis benim beklediğim formatı gerçekten döndürüyor mu?" diye test eder. Üretici tarafında: "Benim servisim, bu sözleşmeye bağlı **tüm** tüketicilerin beklentisini karşılıyor mu?" diye kontrol eder.

Bu testler sürekli entegrasyon sürecine eklenir. Bir geliştirici kodu değiştirdiğinde, sözleşme testleri otomatik çalışır. Kırılma varsa derleme aşamasında yakalanır—üretimde değil, müşteri karşısında değil.

Emniyet kemeri devreye girmiş olur.

### Yönetici bu anda ne düşünür
"Testlerin CI/CD'ye entegrasyonu güzel. Mevcut boru hattımıza nasıl eklenir?"

### Olası soru
Mevcut test altyapımızla uyumlu mu? Ekstra maliyet yaratır mı?

### Süre
55 saniye.

---

## SUNU 07

### İçerik
- **Başlık:** Neden "Emniyet Kemeri"?
- Emniyet kemeri: kazayı **önlemez**, ama hasarı **sınırlar**
- Sözleşme Testi de aynı şekilde: her hatayı durdurmaz, ama entegrasyon kırılmalarını **görünür** kılar
- Takmak 3 saniye alır; takmamak ömür boyu pişmanlık bırakabilir
- Sözleşme testi: kurulum maliyeti **bir kez**, faydası **her dağıtımda**
- Aracı takmak yeterli değil: **doğru takılmış** olması gerekir

### Konuşma metni
Neden emniyet kemeri?

Emniyet kemeri sizi trafik kazasından korumaz. Ama bir kaza olduğunda hasarı dramatik biçimde azaltır. Ve bunu her seferinde, güvenilir şekilde yapar.

Sözleşme Testi de tam olarak böyle çalışıyor. Hiçbir yazılım sizi sıfır hataya götürmez. Ama sözleşme testi entegrasyon kırılmalarını erken ve güvenilir biçimde yakalar—her dağıtımda.

Emniyet kemerini "zaman kaybı" diye takmayan insanlar var. Aynı şekilde "şimdiye kadar sorun olmadı, gerek yok" diyenler de var. Her iki durumda da zarar kaçınılmaz hale geliyor.

Kurulum bir kez yapılır. Faydası her dağıtımda geliyor. Ve tabii ki doğru takılmış olması şart.

### Yönetici bu anda ne düşünür
"Metafor yerinde. Ama pratikte ne kadar efor gerektiriyor?"

### Olası soru
Bu sistemi kurmak ne kadar sürer, ne kadar efor gerektirir?

### Süre
45 saniye.

---

## SUNU 08

### İçerik
- **Başlık:** Teknoloji ve Araçlar
- **Pact:** Tüketici güdümlü sözleşme testi çerçevesi; en yaygın açık kaynak araç
- **Pact Broker:** Sözleşmelerin merkezi yönetim ve dağıtım deposu
- **OpenAPI / AsyncAPI:** Sözleşme tanım standartları (REST ve mesaj tabanlı)
- **Spring Cloud Contract:** Java ekosistemi için alternatif çerçeve
- Mevcut CI/CD araçlarıyla (Jenkins, GitLab CI) entegrasyon sağlanır
- Dil bağımsız: Java, .NET, Python, Node.js desteklenir

### Konuşma metni
Peki hangi araçlarla yapıyoruz?

Ekosistemde en yaygın kullanılan araç **Pact**. Açık kaynak, geniş topluluk desteği var. Tüketici güdümlü sözleşme testini doğrudan destekliyor.

Yanında **Pact Broker** geliyor. Sözleşmelerin merkezi deposu. Hangi sözleşmenin hangi sürümünün hangi ortamda geçerli olduğunu buradan takip ediyorsunuz.

Sözleşme tanımları için **OpenAPI** standardını kullanıyoruz—muhtemelen ekiplerimiz zaten biliyor. Mesaj tabanlı sistemler için ise **AsyncAPI** var.

Java ekosistemi için **Spring Cloud Contract** alternatif bir seçenek. Ekibin teknoloji yığınına göre tercih yapılabilir.

Tüm bu araçlar mevcut Jenkins ya da GitLab CI boru hatlarına kolayca ekleniyor. Dil bağımsız—Java, .NET, Python, Node.js hepsini destekliyor.

### Yönetici bu anda ne düşünür
"Açık kaynak araçlar güzel ama lisans ve destek konusunda dikkatli olmak gerekir."

### Olası soru
Bu araçların kurumsal destek (ticari lisans, güvenlik güncellemeleri) durumu nedir?

### Süre
55 saniye.

---

## SUNU 09

### İçerik
- **Başlık:** Yönetişim Modeli
- Sözleşme sahibi: **tüketen ekip** — ihtiyacı tanımlar
- Sözleşme onaylayıcı: **üreten ekip** — uygulanabilirliği doğrular
- Değişiklik talebi süreci: kırıcı değişiklik (breaking change) bildirimi zorunlu
- Sözleşme deposu erişimi: ekip bazında, rol tabanlı
- İhlal yönetimi: otomatik bildirim ve derleme engelleme (build gate)
- Merkezi koordinasyon: OKF (Orta Katman ve Framework) müdürlüğü

### Konuşma metni
Teknolojiyi kurmak yeterli değil. Kimin ne yapacağını da netleştirmek gerekiyor—yani yönetişim.

Modelimiz şöyle çalışıyor: Sözleşmeyi **tüketen ekip** yazar ve sahiplenir. "Ben bu servisten şunu bekliyorum" diyor. **Üreten ekip** bunu değerlendirip onaylıyor.

Bir ekip serviste kırıcı değişiklik yapacaksa—yani mevcut bir sözleşmeyi bozan bir değişiklik—bunu önceden bildirmek zorunda. Bu bir kural, istisna yok.

İhlaller otomatik olarak yakalanıyor: derleme engelleniyor ve ilgili ekipler bildirim alıyor. Elle müdahale beklenmiyor.

Merkezi koordinasyon OKF müdürlüğümüz tarafından yürütülüyor. Standartları biz belirliyoruz, uygulamayı ekipler yapıyor.

### Yönetici bu anda ne düşünür
"OKF'nin koordinasyon rolü net. Ama ekiplerin buna uyması nasıl sağlanacak?"

### Olası soru
Kırıcı değişiklik bildirimi yapılmazsa ne olur? Yaptırım mekanizması var mı?

### Süre
50 saniye.

---

## SUNU 10

### İçerik
- **Başlık:** Test Stratejisi
- **Seviye 1 — Birim Testi:** Servis iç mantığı; mevcut altyapı
- **Seviye 2 — Sözleşme Testi:** Servisler arası arayüz doğrulama ← **yeni katman**
- **Seviye 3 — Uçtan Uca Test:** Tam iş akışı; seçici ve az sayıda
- Sözleşme testi, uçtan uca test ihtiyacını **azaltır**
- Sahte servis (mock) kullanımını **standartlaştırır**
- Kapsam: tüm REST API ve mesaj tabanlı entegrasyonlar

### Konuşma metni
Sözleşme testini var olan test altyapısına nasıl yerleştiriyoruz?

Üç katlı bir test modelini benimsiyoruz. En alt katta **birim testleri** var—bunlar zaten yapılıyor. En üstte **uçtan uca testler** var—değerli ama yavaş ve bakımı zor.

Ortaya yeni bir katman ekliyoruz: **sözleşme testi**. Bu katman iki servisin birbirine bağlandığı noktayı test ediyor; ancak bunu her iki servisi aynı anda ayağa kaldırmadan yapıyor. Sahte servis kullanıyor—ama bu sahte servis sözleşmeden türetildiği için güvenilir.

Bu yaklaşımın yan faydası şu: uçtan uca test ihtiyacı azalıyor. Entegrasyon noktaları sözleşme testleriyle güvence altına alındığında, uçtan uca testlerin sayısını bilinçli olarak düşürebiliyoruz.

### Yönetici bu anda ne düşünür
"Uçtan uca testlerin azalması demek hem hız hem de maliyet tasarrufu demek."

### Olası soru
Sözleşme testi hangi entegrasyonları kapsamıyor, nerelerde boşluk kalır?

### Süre
55 saniye.

---

## SUNU 11

### İçerik
- **Başlık:** Benimseme Planı
- **Aşama 1:** Farkındalık ve eğitim — tüm ekiplere temel kavramlar (1. ay)
- **Aşama 2:** Pilot — 2–3 gönüllü ekip, seçilmiş entegrasyonlar (2–3. ay)
- **Aşama 3:** Yatay yayılım — pilot çıktılarıyla diğer ekiplere genişleme (4–6. ay)
- **Aşama 4:** Zorunluluk — yeni entegrasyonlarda sözleşme testi standart gereksinim (7. ay+)
- Her aşamada OKF desteği: şablonlar, rehberler, danışmanlık
- Değişim yönetimi: "kural" değil "araç" olarak konumlandırma

### Konuşma metni
Teknolojiyi kurmak ve kuralları belirlemek yetmiyor. Ekiplerin bu yaklaşımı benimsemesi gerekiyor.

Benimseme planımız dört aşamalı.

İlk ayda farkındalık ve eğitim. Ekiplere temel kavramları, araçları ve faydaları anlatıyoruz. Korkutucu değil, destekleyici bir dille.

İkinci ve üçüncü aylarda pilot. İki ya da üç gönüllü ekiple başlıyoruz. Gerçek entegrasyonlar üzerinde çalışıyoruz. Öğrendiklerimizi belgeliyoruz.

Dördüncü ila altıncı aylarda yatay yayılım. Pilot çıktılarını somut şablonlara ve rehberlere dönüştürüyoruz. Diğer ekiplere yayıyoruz.

Yedinci aydan itibaren zorunluluk. Yeni entegrasyonlarda sözleşme testi standart bir gereksinim haline geliyor.

Kritik nokta: bunu bir kural olarak değil, **bir araç** olarak konumlandırıyoruz. "Sizi denetliyoruz" değil, "sizi koruyoruz."

### Yönetici bu anda ne düşünür
"7 ay makul bir zaman çizelgesi. Pilot için kaynak gereksinimi ne?"

### Olası soru
Pilot ekiplerde bu çalışma için ne kadar ek efor bekleniyor?

### Süre
50 saniye.

---

## SUNU 12

### İçerik
- **Başlık:** Başarı Metrikleri
- Entegrasyon kaynaklı üretim olayı sayısı: **hedef %60 azalma** (12 ay; başlangıç değeri 1. ayda ölçülür)
- Entegrasyon hatasının tespit süresi: üretimden CI/CD'ye **çekilmesi**
- Sözleşme kapsamı: tüm REST/mesaj entegrasyonlarının **%80'i** (12 ay)
- Ortalama düzeltme süresi (MTTR): **%40 iyileşme** (sözleşme ihlali fark edilme → çözüm süresi)
- Bağımsız dağıtım oranı: ekiplerin birbirini beklemeden yayınlama sıklığı; **hedef %30 artış**

### Konuşma metni
Başarıyı nasıl ölçeceğiz?

Beş temel metrik belirliyoruz.

Birinci: entegrasyon kaynaklı üretim olayı sayısı. 12 ay içinde %60 azalma hedefliyoruz. Bu en kritik metrik. Başlangıç değerini birinci ayda ölçüyor ve belgeliyoruz.

İkinci: entegrasyon hatasının tespit noktası. Bugün üretimde fark ediliyor; hedef, CI/CD sürecinde yakalamak. Bu niteliksel bir dönüşüm.

Üçüncü: sözleşme kapsamı. 12 ay sonunda tüm entegrasyonların en az %80'i sözleşme testine sahip olmalı.

Dördüncü: ortalama düzeltme süresi. Sözleşme ihlali fark edilmesinden çözümüne kadar geçen süredir — üretim olayı sayısının azalmasından bağımsız ölçülür. %40 iyileşme bekliyoruz.

Beşinci: bağımsız dağıtım oranı. Ekipler birbirini beklemeden ne sıklıkla yayın yapabiliyor? %30 artış hedefliyoruz. Bu metrik ekip özerkliğini ölçüyor.

### Yönetici bu anda ne düşünür
"Metrikler somut ve ölçülebilir. Ama başlangıç değerlerini (baseline) bilmemiz gerekiyor."

### Olası soru
Bu metriklerin mevcut başlangıç değerleri nedir, nasıl ölçeceğiz?

### Süre
50 saniye.

---

## SUNU 13

### İçerik
- **Başlık:** Pilot Çalışma Önerisi
- **Kapsam:** Ödeme servisi ↔ Hesap servisi entegrasyonu
- **Süre:** 6 hafta
- **Ekip:** 2 geliştirici + OKF danışmanlık desteği
- **Çıktı:** Çalışan sözleşme testleri, şablon ve rehber belge, lessons learned raporu
- **Başarı kriteri:** Sözleşme testi CI/CD'ye entegre, en az 1 kırılma erken yakalanmış
- **Risk:** Düşük — mevcut testler değiştirilmiyor, yalnızca ekleniyor

### Konuşma metni
Soyuttan somuta geçelim. Bir pilot çalışma öneriyoruz.

Ödeme servisi ile Hesap servisi arasındaki entegrasyon iyi bir başlangıç noktası. Bu entegrasyon iş açısından kritik, değişim sıklığı yüksek ve iki farklı ekip tarafından yönetiliyor.

Altı haftalık bir çalışma öngörüyoruz. İki geliştirici ve OKF danışmanlık desteğiyle.

Altı hafta sonunda elimizde şunlar olacak: çalışan sözleşme testleri, tekrar kullanılabilir şablon ve rehber belgeler, ve—en önemlisi—bir lessons learned raporu. Bu rapor yatay yayılımın temelini oluşturacak.

Risk düşük: mevcut testlere dokunmuyoruz, sadece yeni bir katman ekliyoruz.

### Yönetici bu anda ne düşünür
"6 hafta ve 2 geliştirici makul. Onay vermek için yeterli bilgiye sahibim."

### Olası soru
Pilot sonucunda devam kararını ne zaman, nasıl vereceğiz?

### Süre
45 saniye.

---

## SUNU 14

### İçerik
- **Başlık:** Yol Haritası
- **1. Ay:** Eğitim ve araç kurulumu; Pact Broker altyapısı
- **2–3. Ay:** Pilot çalışma; ilk sözleşmeler ve testler
- **4–6. Ay:** Yatay yayılım; şablonlar ve standartların yayınlanması
- **7–9. Ay:** Kapsam genişletme; yeni entegrasyonlarda zorunluluk
- **10–12. Ay:** Olgunluk değerlendirmesi; metrik gözden geçirmesi; iyileştirme
- Her adımda geriye dönük uyumluluk korunur

### Konuşma metni
12 aylık yol haritamızı özetle görelim.

Birinci ayda altyapıyı kuruyoruz: Pact Broker, temel eğitimler, ilk standart belgeler.

İkinci ve üçüncü aylarda pilot çalışmayı yürütüyoruz. Öğreniyoruz, belgeliyoruz.

Dördüncü ila altıncı aylarda yatay yayılım başlıyor. Pilot çıktılarını şablona dönüştürüyoruz ve ekiplere sunuyoruz.

Yedinci ila dokuzuncu aylarda yeni entegrasyonlarda sözleşme testi zorunlu hale geliyor.

Onuncu ila on ikinci aylarda olgunluk değerlendirmesi yapıyoruz. Metriklere bakıyoruz, neyin çalışıp neyin çalışmadığını gözden geçiriyoruz.

Her aşamada geriye dönük uyumluluk korunuyor. Kimse bir sabah kalktığında her şeyin değiştiğini görmeyecek.

### Yönetici bu anda ne düşünür
"Aşamalı yaklaşım mantıklı. 12 ay sonunda nerede olacağımızı net görebiliyorum."

### Olası soru
Bu yol haritasında en kritik risk nedir, nasıl yönetilecek?

### Süre
45 saniye.

---

## SUNU 15

### İçerik
- **Başlık:** Özet
- Sorun: Entegrasyon kırılmaları görünmez ve maliyetli
- Çözüm: Sözleşme Yönetimi + Sözleşme Testi = Emniyet Kemeri
- Yaklaşım: Tüketici güdümlü, araç destekli, yönetişimle güçlendirilmiş
- Yatırım: Pilot için 6 hafta, 2 geliştirici
- Beklenti: 12 ayda %60 üretim olayı azalması, ekip özerkliğinde artış
- **Sonraki adım:** Pilot için onay

### Konuşma metni
Son olarak özetleyelim.

Bankacılık sistemlerinde entegrasyon kırılmaları görünmez ama maliyetli bir risk. Bu riski sistematik olarak yönetmek için iki araçtan yararlanıyoruz: Sözleşme Yönetimi ve Sözleşme Testi.

Bu ikili, dijital dönüşümümüzdeki emniyet kemeri.

Başlamak için büyük bir yatırım gerekmez. Pilot için 6 hafta ve 2 geliştirici yeterli. 12 ay sonunda üretim olaylarında %60 azalma ve daha özerk ekipler bekliyoruz.

Sizden tek talebim: pilota onay. Geri kalanını biz yönetiriz.

### Yönetici bu anda ne düşünür
"İkna oldum. Pilot için onay verebilirim."

### Olası soru
Onay sürecini nasıl işleteceğiz?

### Süre
40 saniye.

---

## SUNU 16

### İçerik
- **Başlık:** Teşekkür ve Sorular
- Ali Osman ALATAŞ
- Lider Uzman — Orta Katman ve Framework Çözümleri Müdürlüğü
- Sorularınızı bekliyorum.

### Konuşma metni
Dinlediğiniz için teşekkür ederim. Sorularınızı almaktan memnuniyet duyarım.

### Yönetici bu anda ne düşünür
"Soru sormak istiyorum. Sunum açık ve yeterliydi."

### Olası soru
Tüm sorular açık — pilot onayı, maliyet, ekip etkisi, araç seçimi, zaman çizelgesi.

### Süre
30 saniye.
