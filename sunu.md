# Contract Management & Contract Testing
## Sunum Hazırlığı — 17 Slayt

**Sunum sahibi:** Ali Osman ALATAŞ  
**Ünvan:** Lider Uzman  
**Müdürlük:** Orta Katman ve Framework Çözümleri Müdürlüğü  
**Tahmini süre:** 13–14 dakika

---

## SLAYT 01 — KAPAK

### Slayttaki İçerik

**Ana başlık:**
Dijital Dönüşümde Emniyet Kemeri

**Alt başlık:**
Contract Management & Contract Testing

**En alt:**
Ali Osman ALATAŞ
Lider Uzman
Orta Katman ve Framework Çözümleri Müdürlüğü

---

### Konuşma Metni

Merhabalar. Ben Ali Osman Alataş. Orta Katman ve Framework Çözümleri Müdürlüğü bünyesinde Lider Uzman olarak görev yapıyorum.

Bugün sizlerle Contract Management ve Contract Testing üzerine konuşmak için bir aradayız. Yaklaşık 12 dakika sürecek.

Bankacılık sistemlerinde çok kritik ama çoğu zaman görünmeyen bir riske odaklanacağız. Bu risk her gün yaşanıyor — farkında olmadan üstünden geçiyoruz. Bu sunumda hem bu riski netleştireceğim hem de onu sistematik bir şekilde nasıl yöneteceğimizi anlatacağım.

---

### Yönetici Bu Anda Ne Düşünür
"Emniyet kemeri metaforu ilginç. Dinleyelim."

### Olası Soru
Yok. Henüz değil.

### Süre
15 saniye. Hemen geçin.

---

## SLAYT 02 — KANCA

### Slayttaki İçerik

**Üstte küçük:**
"Bankacılık sistemlerinde her gün yaşanan görünmez bir risk var."

**Ortada büyük soru:**
"Bir Provider değiştiğinde — hangi Consumer'lar habersiz kalır?"

**Altında ikon satırı:**
📱 Mobil · 💻 Web · ☎️ Çağrı Merkezi · 🔁 Backend Servisler · 🌐 Partner Servisler · 🏧 ATM

**Ortaya ikinci soru:**
"Bir değişiklik, kaç domino taşını devirir?"

**En altta kırmızı kutuda:**
"Çoğu zaman bilmiyoruz."

---

### Konuşma Metni

Size bir soru sormak istiyorum.

Sisteminizdeki herhangi bir Provider — yani API sunan bir servis — bu sabah değişse, hangi Consumer'ların etkileneceğini gerçekten biliyor muyuz?

Mobil mi, web mi, çağrı merkezi mi, başka backend servisler mi, partner sistemler mi, ATM mi?

*(Bir saniye duraklayın. Cevap beklemeyin.)*

Çoğu zaman bilmiyoruz. Bu bilgi bazen geliştiricilerin kafasında, bazen eski bir dokümanda, bazen hiçbir yerde.

İki kavramı netleştirelim. Provider, API'yi sağlayan servistir. Consumer ise o API'yi kullanan her uygulama ve servistir. Mobil de consumer, web de consumer, çağrı merkezi de consumer. Hepsi aynı Provider'a bağımlı. Provider değiştiğinde hepsi etkilenebilir.

Bunu domino etkisi gibi düşünün. En temel servislerimizden birinde tek bir alan değişse, hangi kanalın, hangi sistemin ne zaman patlayacağını kesin olarak biliyor muyuz? Maalesef bu bağımlılıkları çoğu zaman ancak incident anında keşfediyoruz.

Bu tek başına kurumsal bir risk.

---

### Yönetici Bu Anda Ne Düşünür
"Doğru. Gerçekten bilmiyoruz. Bu rahatsız edici."

### Olası Sorular

**S:** Peki şimdiye kadar büyük bir sorun yaşadık mı?
**C:** Şimdiye kadar büyük bir kesinti yaşamamış olabiliriz — ama bu şansa güvendiğimiz anlamına geliyor. Birazdan çok somut bir senaryo göstereceğim.

**S:** Elimizde servis envanteri yok mu?
**C:** Envanterimiz var ama servislerin içindeki veri modellerine olan bağımlılıkları canlı ve otomatik takip eden bir mekanizmamız yok. İşte bu eksikliği kapatacağız.

### Süre
30 saniye.

---

## SLAYT 03 — SENARYO GİRİŞİ

### Slayttaki İçerik

**Başlık:**
"Bu Sabah Ne Oldu? — Customer Service Değişti"

**Alt italik:**
"Somut bir örnek. Ama bu sadece bu servisin sorunu değil — her Provider–Consumer ilişkisinde aynı risk var."

**Timeline:**
🕘 09:15 — Customer Service deploy edildi. Tüm testler geçmişti.
🕙 09:25 — Mobil Consumer çalışmıyor. İlk alarm.
🕙 09:30 — Çağrı merkezi Consumer müşteri ekranını açamıyor.
🕙 09:40 — Incident açıldı. Tüm ekipler alarma geçti.

**Alt kırmızı kutuda:**
"Her şey testten geçmişti. Hiçbir hata yoktu."

---

### Konuşma Metni

Somut bir örnek üzerinden gidelim. Ama baştan söyleyeyim — bu özel bir servisin problemi değil. Sisteminizdeki her Provider–Consumer ilişkisinde aynı risk var.

İş biriminden gelen talep sonucu Customer Service'te değişiklikler yapılması için task açıldı. Developer kendine atanan task içeriğine göre geliştirmelerini yaptı.

Sabah 09:15. Customer Service için PR açıldı. Pipeline'da unit testler geçti. Integration testler geçti. Servis ayağa kalktı. Deploy production'a çıktı.

09:25'te ilk alarm geliyor. Mobil Consumer çalışmıyor.

09:30'da çağrı merkezi Consumer müşteri ekranını açamıyor.

09:40'ta incident açıldı. Tüm ekipler alarma geçti.

*(Durun. Bir saniye bekleyin.)*

Hiçbir hata yoktu. Testler geçmişti. Ama production patladı.

Neden?

---

### Yönetici Bu Anda Ne Düşünür
"Tanıdık senaryo. Bu bize de oldu ya da olabilir."

### Olası Soru
Henüz soru sormaz. Merakla bekler.

### Süre
45 saniye.

---

## SLAYT 04 — TEKNİK DEĞİŞİKLİK

### Slayttaki İçerik

**Başlık:**
"Provider Contract'ı Değişti — Consumer'lar Habersiz"

**İki kolon yan yana:**

ÖNCE — Provider Response
```json
GET /api/v1/customer/{id}
{
  "customerId": "123",
  "FullName": "Ali Yılmaz",
  "phone": "05321234567",
  "address": "Istanbul",
  "creditScore": "1500",
  "accounts": [
    { "accountNumber": "TR123", "balance": 1000 }
  ]
}
```

SONRA — Provider Response
```json
GET /api/v1/customer/{id}
{
  "customerId": "123",
  "fullName": "Ali Yılmaz",
  "name": "Ali",
  "surname": "Yılmaz",
  "phones": ["+905321234567", "+905329876543"],
  "addresses": ["Istanbul", "Ankara"],
  "creditScore": 1500,
  "accounts": [
    { "accountNumber": "TR123", "balance": 1000 }
  ]
}
```

**Altta kırmızı maddeler:**
❌ `FullName` → `fullName` *(alan adı değişti)*
❌ `phone` → `phones` *(string → array)*
❌ `address` → `addresses` *(string → array)*
❌ `creditScore` → *(string → integer)*

**Alt italik:**
"Provider için masum bir refactor. Consumer için Breaking Change."

---

### Konuşma Metni

Provider tarafında ne değişti? Teknik olarak bakıldığında tamamen iyi niyetli ve doğru kararlar.

`FullName` yerine `fullName` — daha temiz model. Tek telefon yerine telefon listesi — müşterinin birden fazla telefonu olabilir. Adres de listeye döndü. `creditScore` string'den integer'a çevrildi — zaten sayıydı.

Provider ekibi için bu masum bir refactor.

Şimdi Consumer tarafına bakalım.

Mobil Consumer `FullName` alanını bekliyor. Artık yok. `phone` alanını bekliyor. Artık `phones` array'i var. `creditScore`'u string olarak parse ediyor. Artık integer geliyor.

Mobil çöktü. Çağrı merkezi aynı durumda. Web aynı durumda.

İşte breaking change bu. Provider için masum. Consumer için felaket. Ve Consumer'lar bunu deploy öncesinde bilmiyordu.

Contract Management tam olarak bu koordinasyonu sağlıyor.

---

### Yönetici Bu Anda Ne Düşünür
"Provider haklı. Consumer da haklı. Koordinasyon eksik."

### Olası Soru

**S:** Consumer'ların kendi testleri neden bunu yakalamadı?
**C:** Provider'ın test ortamında Consumer uygulamaları yok. Consumer'ların da bu değişiklikten haberi olmadı. İki ekip birbirinden bağımsız çalıştı — aralarında otomatik koordinasyon mekanizması yoktu. Contract Management tam olarak bu mekanizmayı kuruyor.

### Süre
1 dakika.

---

## SLAYT 05 — ZİNCİRLEME REAKSİYON

### Slayttaki İçerik

**Başlık:**
"Tek Provider. Zincirleme Reaksiyon."

**Ortada Provider kutusu. Etrafında oklar ile yayılan kırmızı Consumer kutuları:**
📱 Mobil — Login çöktü. Müşteri giremez.
💻 Web — Müşteri bilgisi yüklenemiyor.
☎️ Çağrı Merkezi — Müşteri ekranı açılamıyor.
🔁 Account API — Parse hatası. İşlemler duruyor.
🌐 Partner Service — Response uyumsuz. Entegrasyon fail.

**Altta büyük kırmızı:**
"Tek Provider değişti. Beş Consumer etkilendi."

**Alt italik:**
"Ve hiçbiri deploy öncesinde bilmiyordu."

---

### Konuşma Metni

Sonuca bakalım.

Mobil Consumer — login ekranı çöktü. Müşteriler bankaya giremez.
Web Consumer — müşteri bilgisi yüklenemiyor.
Çağrı merkezi Consumer — müşteri ekranı açılamıyor. Çalışanlar müşterilere yardım edemiyor.
Account API Consumer — response'u parse edemiyor. İşlemler duruyor.
Partner Service Consumer — response formatı değişti. Entegrasyon fail ediyor.

*(Durun.)*

Tek bir Provider değişti. Beş Consumer etkilendi. Hepsi aynı anda. Ve hiçbiri deploy öncesinde bilmiyordu.

Bankacılıkta en tehlikeli Consumer çoğu zaman mobildir. Mobil release App Store sürecine bağlı. Güncelleme yavaş. Kullanıcı update etmiyor. Eski versiyonlar aylarca canlıda kalabiliyor. Provider değiştiğinde eski mobil patlar — ve mekanizma yoksa müşteri bunu yaşar.

---

### Yönetici Bu Anda Ne Düşünür
"Müşteri etkisi var. Reputasyon riski var. Bu kabul edilemez."

### Olası Soru

**S:** Rollback yapıldı mı? Ne kadar sürdü?
**C:** Evet rollback yapıldı. Ortalama 1.5 saat. Bu 1.5 saatte mobil müşteriler login olamıyor, çağrı merkezi çalışamıyor, işlemler duruyor. Ve her rollback bir güven kaybı — hem müşteri hem kurum için.

### Süre
45 saniye.

---

## SLAYT 06 — ROOT CAUSE

### Slayttaki İçerik

**Başlık:**
"Neden Oldu?"

**Alt italik:**
"Bu bir geliştirici hatası değildi."

**Dört madde:**
❌ Provider'ın hangi Consumer'ları olduğu **bilinmiyordu**
❌ Breaking Change Consumer'lara **haber verilemedi**
❌ Deploy öncesi **otomatik kontrol yapılmadı**
❌ **Kırılacak mı bilinmeden** canlıya çıkıldı

**Alt mor kutuda:**
"Root cause: Breaking Change tespit edilemedi. Provider–Consumer ilişki haritası yok."

---

### Konuşma Metni

Şimdi kritik soruya gelelim. Neden oldu?

Bu bir geliştirici hatası değildi. Provider ekibi yanlış kod yazmadı. Testler geçti. Sistem çalıştı.

Ama dört basit gerçek var.

Provider'ın hangi Consumer'lara hizmet ettiği bilinmiyordu. Mobil mi, web mi, çağrı merkezi mi, partner sistemler mi — bu bilgi hiçbir sistemde kayıtlı değildi.

Breaking Change Consumer'lara haber verilemedi. Çünkü kimler etkileneceği bilinmiyordu ki haber verilebilsin.

Deploy öncesi "bu değişiklik mevcut Consumer'ları kırıyor mu?" diye soran otomatik kontrol yoktu.

Kırılacak mı bilinmeden canlıya çıkıldı. Production öğretti.

Root cause tek cümle: Breaking Change tespit edilemedi. Provider–Consumer ilişki haritası yok.

Bu iki şey olsaydı — bu incident yaşanmazdı. İşte bu problemi çözmek için tasarlanan mimari Contract Testing.

---

### Yönetici Bu Anda Ne Düşünür
"Basit ama kritik. Bunları neden kurmadık?"

### Olası Soru

**S:** Peki şu an bu görünürlük var mı?
**C:** Şu an sistematik bir Consumer haritamız yok. Bu bilgi kişilerde ve dağınık dokümanlarda. Sunumun devamında bunu nasıl çözeceğimizi göstereceğim.

### Süre
45 saniye.

---

## SLAYT 07 — CONTRACT NEDİR?

### Slayttaki İçerik

**Başlık:**
"Contract Nedir?"

**Üstte tanım kutusu:**
"Consumer'ın Provider'dan beklediği veri modelidir."

**Ortada tablo:**

| Consumer | Protokol | Ne Bekliyor |
|----------|----------|-------------|
| 📱 Mobil | HTTP | `FullName`, `phone`, `creditScore` string |
| 💻 Web | HTTP | `fullName`, `phones` array |
| ☎️ Çağrı Merkezi | HTTP | `FullName`, `phone` |
| 🔁 Account API | gRPC | `GetCustomer` metodu |
| 📨 Bildirim Servisi | Event | `CustomerUpdatedEvent` payload |

**Altta vurgu:**
"Aynı Provider. Beş farklı Consumer. Beş farklı contract."

---

### Konuşma Metni

Çözümün merkezindeki kavrama gelelim. Contract.

Contract, Consumer'ın Provider'dan beklediği veri modelidir. Servisler arası iletişimi sadece bir URL çağrısı değil, dijital bir sözleşme olarak tanımlıyoruz.

Tabloya bakalım.

Mobil Consumer HTTP üzerinden Provider'a istek atıyor. `FullName`, `phone`, `creditScore`'u string olarak bekliyor. Bu bir contract.

Web Consumer aynı Provider'ı kullanıyor ama daha yeni versiyona göre `fullName` ve `phones` array bekliyor. Bu da bir contract. Ama farklı bir contract.

Çağrı merkezi Consumer eski versiyona göre çalışıyor.

Account API gRPC üzerinden `GetCustomer` metodunu çağırıyor. Bu da bir contract.

Bildirim servisi Provider'ın yayınladığı `CustomerUpdatedEvent`'i dinliyor. Bu da bir contract.

Dikkat edin. Aynı Provider. Beş farklı Consumer. Beş farklı beklenti. Beş farklı contract.

Provider bunların hepsini bilmeden değişiklik yapıyor. İşte sorun buradan çıkıyor.

---

### Yönetici Bu Anda Ne Düşünür
"Sözleşme fikri net. HTTP, gRPC, Event — hepsini kapsıyor."

### Olası Soru

**S:** Bu contract'ları kim yazacak? Developer mı?
**C:** Mümkün olduğunca otomatik üretilecek. Geliştiriciye ekstra manuel iş yükü bindirmeyeceğiz. Bunu bir sonraki slaytlarda göstereceğim.

### Süre
1 dakika.

---

## SLAYT 08 — INTERACTION NEDİR?

### Slayttaki İçerik

**Başlık:**
"Bir Contract İçinde Ne Var? — Interaction"

**Alt italik:**
"Her endpoint, her gRPC metodu, her event ayrı bir interaction'dır."

**Ortada Pact dosyası örneği:**

```
Consumer : Mobil_App
Provider : Customer_Service

Interaction 1 — HTTP
  İstek   : GET /api/v1/customer/{id}
  Beklenen: { "FullName": string, "phone": string }

Interaction 2 — HTTP
  İstek   : POST /api/v1/update-phone
  Beklenen: 200 OK

Interaction 3 — Event
  Event   : CustomerCreated
  Beklenen: { "customerId": integer }
```

**Alt vurgu:**
"Üç interaction. Tek Pact dosyası. Mobil'in Customer Service'ten beklediği her şey burada."

---

### Konuşma Metni

Contract kavramını anladık. Şimdi biraz daha somutlaştıralım.

Bir Consumer birden fazla endpoint kullanıyor olabilir. Birden fazla event dinliyor olabilir. Her biri için ayrı ayrı contract yazmıyoruz. Bunların hepsi tek bir Pact dosyasında toplanıyor.

Her endpoint, her gRPC metodu, her event birer interaction olarak kaydediliyor.

Örneğe bakalım. Mobil'in Customer Service için ürettiği Pact dosyasında üç interaction var.

Birinci interaction HTTP. Mobil `GET /api/v1/customer/{id}` endpoint'ini çağırıyor ve response'ta `FullName` string ve `phone` string bekliyor.

İkinci interaction yine HTTP. `POST /api/v1/update-phone` çağırıyor ve 200 OK bekliyor.

Üçüncü interaction bir event. Mobil `CustomerCreated` eventini dinliyor ve payload'da `customerId` integer bekliyor.

Bu üç interaction tek bir Pact dosyasında toplanıyor. Mobil'in Customer Service'ten beklediği her şey burada kayıtlı.

Customer Service'te bir değişiklik olduğunda sistem bu dosyayı alıyor, her interaction'ı test ediyor ve kırılan var mı kontrol ediyor.

---

### Yönetici Bu Anda Ne Düşünür
"Somut. Anlıyorum. Bir dosyada her şey var."

### Olası Sorular

**S:** Her Consumer için ayrı dosya mı olacak?
**C:** Evet. Her Consumer kendi Pact dosyasını üretiyor. Pact Broker tüm dosyaları merkezi olarak saklıyor. Customer Service değiştiğinde sistem tüm Consumer'ların dosyalarını çekip test ediyor.

**S:** Bu dosyayı kim güncelleyecek?
**C:** Consumer'ın kodu değiştiğinde Pact dosyası otomatik yeniden üretiliyor. Manuel güncelleme yok.

### Süre
1 dakika.

---

## SLAYT 09 — CONTRACT REGISTRY NASIL OLUŞTURULUR?

### Slayttaki İçerik

**Başlık:**
"Contract Registry Nasıl Oluşturulur?"

**Alt italik:**
"Excel ile değil — canlı trafik ile."

**Üç kaynak kutusu soldan sağa okla bağlı:**

**1. API Gateway Logları**
Tüm servis çağrıları buradan geçer.
Kim kimi çağırıyor otomatik görünür.
*Teknik adı: Service Dependency Mapping*

**2. Servis Şemaları**
OpenAPI / Swagger dosyaları
Proto dosyaları
Event tanımları

**3. Framework Interceptor**
HTTP çağrısında araya girer
gRPC kullanımında araya girer
Event tüketiminde araya girer
Hem "kim çağırdı" hem "hangi veriyi bekledi" yakalar

**Sağda sonuç kutusu — Contract Registry:**
```
Mobil       → Customer Service
Web         → Customer Service
Çağrı Mrk.  → Customer Service
Account API → Customer Service
```

**Alt not italik:**
"İlk gün %100 olmayabilir. Sistem çalıştıkça harita tamamlanır."

---

### Konuşma Metni

Şimdi en kritik soruya gelelim. Contract Registry nasıl oluşturacağız? Customer Service'i kimlerin kullandığını bilmiyoruz — bu bilgiyi nasıl öğreneceğiz?

Excel'e yazmayacağız. Manuel kayıt tutmayacağız. Çünkü manual şeyler güncelliğini kaybeder. Kişi değişir, bilgi uçar.

Bu işlemin teknik adı Service Dependency Mapping. Üç kaynaktan otomatik çıkarıyoruz.

Birincisi API Gateway logları. Tüm servis çağrıları zaten oradan geçiyor. Mobil Customer Service'e istek atıyor — gateway görüyor. Bu loglardan kim kimi çağırıyor haritası otomatik çıkıyor. Mevcut sistemleri hiç değiştirmeden.

İkincisi servis şemaları. OpenAPI dosyaları, proto dosyaları, event tanımları — bunlar zaten var. Taranıyor ve bağımlılıklar çıkarılıyor.

Üçüncüsü framework interceptor. Servis HTTP çağrısı yaptığında, gRPC kullandığında, event tükettiğinde framework araya giriyor. Sadece "kim kimi çağırdı" bilgisini değil, "hangi veriyi bekledi" bilgisini de yakalıyor. Bu ikisi birlikte contract'ı oluşturuyor.

Önemli not: İlk gün yüzde yüz olmayacak. Mevcut sistemleri kaydetmek zaman alacak. Ama sistem çalıştıkça harita tamamlanıyor. Gün geçtikçe körleşmek yerine gün geçtikçe netleşiyoruz.

---

### Yönetici Bu Anda Ne Düşünür
"Mevcut sisteme dokunmadan başlıyor. Kademeli. Akıllıca."

### Olası Sorular

**S:** Runtime'da performans kaybı olur mu?
**C:** Hayır. Interceptor asenkron ve hafif çalışır. Ağır kontroller CI/CD aşamasında yapılır. Production'a ekstra yük binmez.

**S:** Gateway dışında kalan internal çağrılar ne olacak?
**C:** Internal çağrılar için framework interceptor devreye giriyor. Gateway dışında kalan her çağrı framework üzerinden yakalanıyor. İkisi birlikte tam kapsamı sağlıyor.

### Süre
1 dakika.

---

## SLAYT 10 — CONTRACT NASIL OLUŞUR?

### Slayttaki İçerik

**Başlık:**
"Contract Nasıl Oluşur?"

**Alt italik:**
"Otomatik. Build-time. İki katmanlı koruma."

**Üstte araç tablosu:**

| Protokol | Araç | Nasıl Çalışır |
|----------|------|----------------|
| HTTP | Pact + oasdiff | Consumer testi yazar → Pact otomatik üretir |
| gRPC | buf | Proto değişince buf otomatik kontrol eder |
| Event | Pact Message | Consumer testi yazar → schema otomatik üretir |

**Ortada iki kutu yan yana:**

**Proaktif — Pact**
```
Consumer testi yazar
        ↓
CI'da test çalışır
        ↓
Pact contract üretir
        ↓
Pact Broker'a publish edilir
```

**Reaktif — Framework Interceptor**
```
Developer test yazmasa bile
        ↓
Framework HTTP/gRPC/Event çağrısını yakalar
        ↓
Şemayı otomatik çıkarır
        ↓
Registry'ye asenkron gönderir
```

**Alt vurgu kutusunda:**
"Sistemi sadece geliştirici disiplinine bırakmıyoruz.
Test yazarsa Pact yakalar.
Test yazmasa bile framework interceptor yakalıyor."

**Alt not italik:**
"Contract üretimi build-time'da olur. Production'a sıfır ek yük."

---

### Konuşma Metni

Bağımlılık haritası oluştu. Peki contractlar nasıl üretiliyor?

Prensip aynı: otomatik üretim, build-time. Production'a ekstra yük yok.

Protokol bazında anlatayım.

HTTP için Pact ve oasdiff birlikte çalışıyor. Mobil ekibi bir kez consumer testi yazar. Bu test Customer Service'e mock üzerinden istek atar ve beklediği response'u tanımlar. Test CI'da çalıştığında Pact otomatik olarak contract dosyası üretir ve Pact Broker'a gönderir. Mobil ekibi bir daha bu işe bakmaz — değişiklik olduğunda sistem otomatik test eder.

gRPC için buf kullanıyoruz. Proto dosyası zaten contract'ın kendisi. Buf bir önceki versiyonla otomatik karşılaştırıyor.

Event için Pact Message. Consumer hangi event payload'ını beklediğini test olarak yazıyor. Pact bunu kaydediyor.

Şimdi çok önemli bir noktaya gelelim. Pact gibi araçlar harika ama sadece geliştiricinin test yazma disiplinine güvenirsek sistemde açıklar kalabilir. Bizim çözümümüz çift taraflı koruma.

Geliştiriciye Pact ile test yazma imkânı veriyoruz — bu proaktif. Test yazmasa bile framework interceptor devreye giriyor ve contract'ı otomatik oluşturuyor — bu reaktif. İnsan hatasını sistem tasarımıyla minimize ediyoruz.

---

### Yönetici Bu Anda Ne Düşünür
"Sadece araç değil, sistem tasarımı var. Düşünülmüş."

### Olası Sorular

**S:** Hangi tool'ları kullanacağız?
**C:** Tool seçimini kurum standartlarımıza göre netleştirebiliriz. Ama ana değer tool'dan bağımsız: contract'ı otomatik üretmek, merkezi tutmak ve CI/CD'de doğrulatmak.

**S:** gRPC'de Pact çalışmıyor muydu?
**C:** Çok doğru. Pact şu an .NET'te gRPC'yi tam desteklemiyor. Bu yüzden gRPC için buf seçtik — proto dosyası zaten contract'ın kendisi olduğu için buf üzerine çok temiz oturuyor.

### Süre
1 dakika 30 saniye.

---

## SLAYT 11 — DEPLOY KAPISI

### Slayttaki İçerik

**Başlık:**
"Deploy Kapısı — Uyumsuz Kod Canlıya Çıkamaz"

**Merkezi akış:**
```
Provider değişiklik yaptı
        ↓
CI Pipeline tetiklendi
        ↓
Registry'den consumer contractları çekildi
        ↓
Mock-based Verification çalıştı:

Mobil Consumer         → ❌ FAIL
Web Consumer           → ✅ PASS
Çağrı Merkezi Consumer → ❌ FAIL
        ↓
🛑 DEPLOY DURDURULDU
        ↓
Ekip bilgilendirildi:
"Mobil ve Çağrı Merkezi etkileniyor"
```

**Altta iki kural kutusu yan yana:**

**Kural 1:**
"Contract yoksa → Deploy yok"

**Kural 2:**
"Breaking Change varsa ve yeni versiyon yoksa → Deploy yok"

**Alt yeşil kutuda:**
"can-i-deploy: Tüm Consumer'lar hazır mı? → Hayır → Deploy yok."

---

### Konuşma Metni

Ve en kritik noktaya geldik. Deploy kapısı.

Provider değişiklik yaptı. CI pipeline tetiklendi. Registry'den tüm Consumer contractları çekildi. Sistem şunu soruyor: "Bu değişiklik Mobil'i kırıyor mu? Çağrı merkezini kırıyor mu?"

Ve burada önemli bir detay var. Gerçek sorgu atılmaz. Buna Mock-based Verification denir. Consumer tarafında gerçek Provider yerine bir Mock Server çalışır. Kodun bu Mock'a attığı istek sözleşmeye uyuyor mu diye bakılır. Provider tarafında ise registry'deki contract alınır, Provider'a replay yapılır ve cevap beklentiyle karşılaştırılır.

Mobil Consumer — fail. Çağrı merkezi Consumer — fail. Web Consumer — pass.

Pipeline şunu söyledi: "Mobil ve Çağrı Merkezi etkileniyor. Deploy yapılamaz." Ekip bilgilendirildi.

Customer Service production'a çıkmadı. Consumer'lar patlamadı. Müşteri etkilenmedi.

İki kural bu kapıyı yönetiyor. Birincisi: contract yoksa deploy yok. İkincisi: breaking change varsa ve yeni versiyon açılmamışsa deploy yok. Developer'dan yeni versiyon oluşturması istenir.

Bu `can-i-deploy` komutu ile yönetiliyor. Registry'ye soruyor: "Tüm Consumer'lar bu Provider versiyonuyla uyumlu mu?" Hayır cevabı gelirse deployment durduruldu.

Şunu vurgulayayım: Bu sistem hızı düşürmüyor. Şu an bizi yavaşlatan şey production'da patlayan sistem ve rollback süreci. Pipeline'a eklenen birkaç dakika bize canlıda saatler ve itibar kazandırır.

---

### Yönetici Bu Anda Ne Düşünür
"İşte bu bizi korur. Peki acil durumda ne olur?"

### Olası Sorular

**S:** Acil hotfix gerekirse ne yapacağız?
**C:** Acil durumlar için override yetkisi olabilir. Ama bu bilinçli risk yönetimi ve izlenebilirlik ile yapılır. Yani kuralı delmek değil, risk alıp kayıt altına almak.

**S:** Her değişiklikte deploy bekleyecek mi? Hız düşmez mi?
**C:** Breaking change olmayan değişikliklerde — backward compatible eklemeler, bug fix'ler — pipeline anında geçiyor. Sadece gerçekten Consumer kıran değişikliklerde duruyor. Hızı değil, sadece riski durduruyor.

### Süre
45 saniye.

---

## SLAYT 12 — ZOR SORULAR BÖLÜM 1

### Slayttaki İçerik

**Başlık:**
"Consumer Yetişemezse? Mobil Sorunu."

**Alt italik:**
"Bankacılıkta en riskli Consumer çoğu zaman mobildir."

**Sol — Problem:**
Mobil App Store sürecine bağlı.
Güncelleme yavaş. Kullanıcı update etmiyor.
Eski versiyonlar aylarca canlıda.

**Sağ — Üç çözüm:**

**1. Provider Versioning**
```
Provider v1 → eski contract (Mobil kullanır)
Provider v2 → yeni contract (Web kullanır)
```
Grace period → Tüm Consumer'lar geçince v1 kapanır.
*Sunset Policy: Veriyle karar veriyoruz, tahminle değil.*

**2. Backward Compatible Değişiklik**
Eski alanlar silinmez. Yeni alanlar eklenir.
Kimse etkilenmez. Versioning'e gerek kalmaz.

**3. Feature Flag**
Yeni davranış kapalı gelir.
Consumer hazır olunca açılır.

**Alt vurgu:**
"Event'lerde breaking change yapılmaz — yeni event yayınlanır."

---

### Konuşma Metni

Şimdi gerçek hayatın zorlu sorularına gelelim. Bunları siz sormadan önce ben sormak istiyorum.

Birinci senaryo: Provider hazır ama Mobil Consumer yetişemedi. Ne yapacağız? Provider bekleyecek mi?

Hayır. Üç seçeneğimiz var.

Birincisi Provider versioning. Provider iki versiyonu paralel çalıştırır. v1 eski contract'ı sunar, v2 yenisini. Mobil hazır olana kadar v1'den okumaya devam eder. Grace period belirlenir. Bu süre sonunda v1 kaldırılır.

Peki v1 ne zaman kapatılacak, kim karar verecek? Contract Registry bize söylüyor. Hangi Consumer hâlâ v1 kullanıyor — registry'de görünüyor. Tüm Consumer'lar v2'ye geçtiğinde v1 kapatılıyor. Buna Sunset Policy diyoruz. Veriyle karar veriyoruz, tahminle değil.

İkincisi backward compatible değişiklik. Eski alanları silmiyoruz, yeni alanları ekliyoruz. Hem eski hem yeni Consumer çalışmaya devam eder. Versioning'e bile gerek kalmaz.

Üçüncüsü feature flag. Yeni davranış kapalı gelir. Consumer hazır olunca açılır.

Breaking change'ler sistem tarafından otomatik yakalanır ve developer'a bildirilir. Versiyonlamayı developer bilinçli yapar. Ama breaking change varsa sistem bunu zorlar — bypass edemez.

Ve burada çok önemli bir not: Event'lerde durum farklıdır. HTTP ve gRPC'de versioning ve contract testing birlikte çalışır. Ama event'lerde breaking change yapılmaz. Bunun yerine yeni bir event yayınlanır. Eski event'i tüketenler etkilenmez.

---

### Yönetici Bu Anda Ne Düşünür
"Seçenekler var. Esnek ama kontrollü."

### Olası Soru

**S:** v1 sonsuza kadar açık mı kalacak?
**C:** Hayır. Sunset Policy ile yönetiyoruz. Contract Registry bize hangi Consumer'ın hâlâ v1 kullandığını gösteriyor. Son Consumer da geçtiğinde v1 kapatılıyor. Veriyle karar veriyoruz.

### Süre
1 dakika 30 saniye.

---

## SLAYT 13 — ZOR SORULAR BÖLÜM 2

### Slayttaki İçerik

**Başlık:**
"Dış Consumer'lar ve Standart"

**İki bölüm yan yana:**

**Sol — Kontrol Dışı Consumer'lar:**
Partner bankalar · Devlet servisleri · Üçüncü parti uygulamalar

Kontrol dışı. Tarih değiştirilemez. Regülasyon var.

Çözüm:
```
Provider v1 → Dış Consumer'lar (Contract Freeze)
Provider v2 → İç Consumer'lar
```
"Regülasyonlu servislerde breaking change yapılmaz.
Contract Freeze uygulanır."

**Sağ — Standart Nasıl Sağlanır:**

🔧 Framework → Otomatik üretir
*Standart yazmakla değil, kullanmakla sağlanır*

🔄 Pipeline → Governance Check
*Contract yoksa build fail. Geçemez.*

📋 Registry → Merkezi kontrol

👥 Framework Ekibi → Altyapıyı kurar, kuralları belirler
*Her ekip içeriğinden, framework ekibi standarttan sorumlu*

**Alt vurgu:**
"Yazılı kural değil — otomatik kontrol."

---

### Konuşma Metni

İkinci zor senaryo: Provider'ı partner bir banka ya da devlet servisi kullanıyor. Tarih değiştirilemez. Regülasyon var. Ne yapacağız?

Bu en kritik senaryo ve tek sürdürülebilir çözüm versioning.

v1 dış Consumer'lar için stabil kalır — buna Contract Freeze diyoruz. İç dünya için v2 açılır. Regülasyonlu servislerde breaking change aynı sözleşme üstünde doğrudan yapılmaz. Bu bir yönetişim kararıdır. Contract Management bunu sistematik hale getirir.

Şimdi ikinci soru: Her ekip farklı yaparsa standart nasıl sağlanacak?

İnsan disiplinine bırakırsak ölçeklenmez. Bu yüzden şu dört mekanizma devreye giriyor.

Framework otomatik üretir. Geliştirici bizim framework'ün sunduğu merkezi kütüphaneleri kullandığında contract zaten built-in olarak üretiliyor. Standart yazmakla değil, kullanmakla sağlanıyor.

Pipeline zorunlu kılıyor. Contract publish edilmemişse CI/CD'deki Governance Check adımında build fail oluyor. Geçemiyor.

Registry merkezi kontrol sağlıyor. Her şey tek yerden görünüyor.

Framework ekibi yönetiyor. Altyapıyı biz kuruyoruz, kuralları biz belirliyoruz. Her ekip kendi servisinin içeriğinden sorumlu — ama standarttan framework ekibi sorumlu.

Sonuç: Yazılı kural değil, otomatik kontrol.

---

### Yönetici Bu Anda Ne Düşünür
"Platform ekibi merkezi kontrol sağlıyor. Governance var. Güvenilir."

### Olası Sorular

**S:** Contract Registry'de kayıt yoksa ne olacak?
**C:** "No contract, no deploy" kuralını bir günde açmayız. Önce izler ve keşfederiz. Yeni servislerde zorunlu kılarız. Registry olgunlaştıkça deploy kapısını aktif ederiz. Sistemi durdurmadan kademeli geçiş yaparız.

**S:** Her ekip ayrı ayrı mı yapacak? Standart bozulmaz mı?
**C:** Hayır. Framework built-in yapıyor. Geliştirici sadece framework'ü kullanıyor — geri kalanı otomatik. Kullanmayı seçemez çünkü pipeline'da Governance Check var.

### Süre
1 dakika 30 saniye.

---

## SLAYT 14 — ÖNCE NE YAPMALIYIZ?

### Slayttaki İçerik

**Başlık:**
"Önce Ne Yapmalıyız?"

**Alt italik:**
"Zamansal değil — öncelik sırası."

**Üç adım soldan sağa okla bağlı:**

**Adım 1: Görünürlük**
Service Dependency Mapping
Gateway log analizi
Servis şema taraması
Framework interceptor kurulumu
→ "Kim kimi tüketiyor — sisteme kayıt altına alıyoruz."

**Adım 2: Otomatik Tespit**
oasdiff PR pipeline entegrasyonu
Pact Broker kurulumu
İlk pilot: Customer Service ↔ Mobil Consumer
→ "Breaking Change PR'da yakalanıyor."

**Adım 3: Deploy Kapısı**
can-i-deploy entegrasyonu
Branch policy zorunlu
gRPC ve Event kapsama alınıyor
→ "Consumer hazır değilse Provider deploy olamaz."

**Alt vurgu kutusunda:**
"Adım 1 tamamlandığında — bu sabahki senaryo zaten engellenirdi."

---

### Konuşma Metni

Peki nereden başlayacağız?

Zamansal bir roadmap yerine öncelik sırasını kuralım.

Önce görünürlük. Hiçbir şey yapmadan önce hangi Consumer'ın hangi Provider'ı tükettiğini bilmemiz gerekiyor. Gateway loglarını analiz ediyoruz. Servis şemalarını tarıyoruz. Framework interceptor'ı kuruyoruz. İlk Consumer haritasını çıkarıyoruz. Bu adımı tamamladığımızda Provider değişikliklerinin kimi etkileyeceği sisteme kayıtlı hale gelir.

Sonra otomatik tespit. oasdiff PR pipeline'a ekleniyor. Pact Broker kuruluyor. İlk pilot olarak en kritik Provider ile Mobil Consumer arasındaki contract test ediliyor. Bu adımı tamamladığımızda breaking change PR'da yakalanıyor — koda bile girmiyor.

Son olarak deploy kapısı. can-i-deploy devreye giriyor. Branch policy zorunlu hale geliyor. gRPC ve Event da kapsama alınıyor. Bu adımı tamamladığımızda Consumer hazır değilse Provider deploy olamıyor.

Kritik not: Sadece birinci adımı tamamlasaydık bile bu sabahki senaryoda etki analizi yapılabilir, koordinasyon sağlanabilirdi. İlk adım bile büyük fark yaratıyor.

---

### Yönetici Bu Anda Ne Düşünür
"Somut. Sıralı. İlk adım bile değer katıyor."

### Olası Soru

**S:** Kaç kişi kaynak gerekiyor?
**C:** İlk iki adım mevcut ekiple başlayabilir. Mevcut pipeline'a ekleme yapıyoruz, sıfırdan değil. Deploy kapısı devreye girince Consumer ekiplerinden katkı gerekir — ama bu ekstra iş değil, zaten ihtiyaç olan testlerin standardize edilmesi.

### Süre
1 dakika 30 saniye.

---

## SLAYT 15 — BAŞARI KRİTERLERİ

### Slayttaki İçerik

**Başlık:**
"Başarıyı Nasıl Ölçeceğiz?"

**Beş KPI kartı:**

📉 Provider kaynaklı incident azalır
Breaking Change'den kaynaklanan kesintiler sıfıra yaklaşır.

📱 Mobil Consumer crash azalır
API değişikliğinden kaynaklanan mobil hatalar biter.

🛡️ Deploy güvenliği artar
Breaking Change PR'da yakalanır. Production'a ulaşmaz.

🗺️ Consumer görünürlüğü sağlanır
Tüm Provider–Consumer ilişkileri canlı ve güncel şekilde bilinir.

🚀 Rollback süresi düşer
1.5 saat → 5 dakika. Çünkü o deployment zaten engellendi.

**Alt vurgu:**
"Hız ve güven birlikte artar. Bunlar çelişmez."

---

### Konuşma Metni

Başarıyı nasıl ölçeceğiz?

Provider kaynaklı incident azalır. Breaking Change'den kaynaklanan kesintiler sıfıra yaklaşır. Sabah 09:25'teki alarm gelmez.

Mobil Consumer crash azalır. API değişikliğinden kaynaklanan mobil hatalar biter. Müşteri bu hatayı yaşamaz.

Deploy güvenliği artar. Breaking Change PR'da yakalanır. Production'a ulaşmaz. Rollback gerekmez.

Consumer görünürlüğü sağlanır. Hangi Consumer'ın hangi Provider'ı tükettiği artık bilinir. Provider değişmeden önce etki analizi yapılabilir.

Ve en güçlü metrik: Rollback süresi 1.5 saatten 5 dakikaya iner. Çünkü o deployment zaten engellendi. Rollback'e gerek kalmadı.

Bir şeyin altını çizmek istiyorum. Bu sistem hız ile güveni çeliştirmiyor — ikisini birleştiriyor. Kontrollü hareket eden ekip daha hızlı hareket eder. Çünkü geri adım atmıyor.

---

### Yönetici Bu Anda Ne Düşünür
"Ölçülebilir. Somut. İkna edici."

### Olası Soru

**S:** Bu metrikleri nasıl takip edeceğiz?
**C:** Pipeline raporları ile breaking change sayısı, registry ve broker panelleri ile contract uyumu, incident kayıtları ile production etki — üçü birlikte takip ediliyor.

### Süre
45 saniye.

---

## SLAYT 16 — KAPANIŞ

### Slayttaki İçerik

Koyu arka plan. Sol mor aksan çizgisi.

**Üstte:**
"09:15 deploy edildi.
09:25 Consumer'lar patladı.
1.5 saat kesinti."

**Ortada büyük:**
"Bu sistem olsaydı —
Consumer'lar patlamazdı."

**Altında:**
"Şu an her Provider değişikliği bir risk taşıyor.
Bu sistem kurulduktan sonra her değişiklik kontrollü."

**En altta:**
"Riski insana değil, sisteme bırakmak."

**En alt ince yazı:**
"En kritik zorluk teknik değil — sahiplik ve koordinasyon.
Bu alanı bilerek yöneteceğiz."

---

### Konuşma Metni

Sabah 09:15'te Provider deploy edildi. 09:25'te Consumer'lar patladı. 1.5 saat kesinti. Müşteriler etkilendi.

Bu sistem olsaydı ne olurdu?

Provider deploy etmek isterdi. Pipeline çalışırdı. Mobil Consumer contract fail ederdi. Deploy durdurulurdu. Ekip bilgilendirilirdi. Consumer'lar patlamazdı. Müşteri etkilenmezdi.

*(Durun.)*

Şu an her Provider değişikliği bir risk taşıyor. Bu sistem kurulduktan sonra her değişiklik kontrollü.

Farkı yaratan tek şey: riski insana değil, sisteme bırakmak.

*(Kısa bir duraklama.)*

Son bir şey eklemek istiyorum. Bu sistemi tasarlarken en kritik zorluk teknik değil — Consumer ekipleri arası sahiplik ve iletişim koordinasyonu. Bu alanı bilerek yöneteceğiz. Çünkü sürdürülebilirlik burada kazanılıyor.

Sorularınızı almaya hazırım.

---

### Yönetici Bu Anda Ne Düşünür
"Net. Güçlü bitiş. Hem teknik hem organizasyonel düşünüyor. Çözüm Mimarı gibi konuştu."

### Olası Sorular

**S:** Mevcut çalışan sistemlere ne olacak?
**C:** Mevcut çalışan sisteme dokunmuyoruz. Yeni değişikliklerden başlıyoruz. Kademeli — önce en kritik Provider'lar, sonra yaygınlaştırma.

**S:** Bu sistemi kim yönetecek?
**C:** Framework ekibi. Registry'yi biz yönetiyoruz, standartları biz belirliyoruz, pipeline kurallarını biz koyuyoruz. Consumer ekipleri kendi testlerini ve uyumluluklarını sahipleniyor.

### Süre
30 saniye.

---

## SLAYT 17 — TEŞEKKÜR

### Slayttaki İçerik

**Ortada büyük:**
Teşekkürler

**Alt:**
ALİ OSMAN ALATAŞ
osman.alatas@albarakatech.com
Orta Katman ve Framework Çözümleri Müdürlüğü

---

### Konuşma Metni

Dinlediğiniz için teşekkür ederim. Sorularınız varsa almaktan memnuniyet duyarım.

### Süre
15 saniye.

---

## ⏱️ Süre Tablosu

| # | Slayt | Süre |
|---|-------|------|
| 01 | Kapak | 15 sn |
| 02 | Kanca | 30 sn |
| 03 | Senaryo girişi | 45 sn |
| 04 | Teknik değişiklik | 1 dk |
| 05 | Zincirleme reaksiyon | 45 sn |
| 06 | Root cause | 45 sn |
| 07 | Contract nedir | 1 dk |
| 08 | Interaction nedir | 1 dk |
| 09 | Registry nasıl oluşur | 1 dk |
| 10 | Contract nasıl oluşur | 1.5 dk |
| 11 | Deploy kapısı | 45 sn |
| 12 | Zor sorular 1 | 1.5 dk |
| 13 | Zor sorular 2 | 1.5 dk |
| 14 | Önce ne yapmalıyız | 1.5 dk |
| 15 | Başarı kriterleri | 45 sn |
| 16 | Kapanış | 30 sn |
| 17 | Teşekkür | 15 sn |
| **Toplam** | | **~13-14 dk** |

---

## 📚 Terimler Sözlüğü

| Terim | Açıklama |
|-------|----------|
| Provider | API sunan servis |
| Consumer | O API'yi kullanan servis/uygulama |
| Contract | Provider ve Consumer arasındaki veri alışveriş formatının dijital anlaşması |
| Contract Management | Sözleşmelerin yaşam döngüsünün yönetilmesi |
| Contract Testing | Değişiklik yapıldığında sözleşmenin hala geçerli olup olmadığının test edilmesi |
| Contract Registry | Tüm sözleşmelerin tutulduğu merkezi depo (Pact Broker) |
| Interaction | Bir contract içindeki tek bir endpoint/metot/event etkileşimi |
| Breaking Change | Geriye dönük uyumluluğu bozan değişiklik |
| Backward Compatibility | Eski kodun yeni versiyonla çalışmaya devam etmesi |
| API Versioning | Aynı servisin farklı versiyonlarının paralel sunulması |
| Consumer-Driven Contract Testing | Test sürecinin Consumer beklentileri üzerinden başlatılması |
| Service Dependency Mapping | Servisler arası bağımlılık haritasının çıkarılması |
| Feature Flag | Yeni özelliği kademeli olarak açmak için kullanılan teknik |
| Contract Freeze | Bir sözleşme versiyonunun artık değiştirilemez hale getirilmesi |
| Sunset Policy | Eski versiyonların ne zaman kapatılacağını belirleyen politika |
| can-i-deploy | CI/CD'de "deploy edebilir miyim?" sorusunu Registry'ye soran komut |
| Mock-based Verification | Gerçek sorgu atmadan Mock Server üzerinden contract doğrulama |
| Pact / Pact File | Consumer-driven contract testing aracı ve sözleşme dosya formatı |
| Provider Verification | Provider'ın Consumer beklentilerine uyduğunu kendi pipeline'ında teyit etmesi |
| Semantic Versioning | 1.2.3 (Major.Minor.Patch) formatında versiyon yönetimi |
