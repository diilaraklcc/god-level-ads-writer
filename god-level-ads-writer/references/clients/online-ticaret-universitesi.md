# Müşteri Profili: Online Ticaret Üniversitesi (Digience Akademi dahil)

_Oluşturulma: 2026-11 | Kaynak: Kullanıcı (ekip içi reklam yazım pratiği) | Durum: `[TESTED]` CTA mimarisi ekip pratiğinde kullanılıyor; ses tonu kalibrasyonu için örnek senaryolar bekleniyor_

> Bu dosya, kullanıcı **Online Ticaret Üniversitesi**, **OTÜ** veya **Digience / Digience Akademi**
> için reklam istediğinde otomatik okunur. Türkiye Modu (`../turkey-market.md`) her zaman
> birlikte açıktır. Bu dosyadaki kurallar, SKILL.md'deki genel kurallarla çatışırsa **bu dosya kazanır**.

---

## 1. Kimlik ve Reklam Türleri

- **Pazar:** Türkiye, Türkçe. Hitap: **sen**.
- **Alan:** E-ticaret, girişimcilik, dijital pazarlama ve kişisel gelişim eğitimleri.
- **Reklam türleri (sıklık sırasıyla):**
  1. **Lansman reklamları:** Ön lansman (bekleme listesi), kayıtların açılışı, kapanış/son gün
  2. **Eğitim satış reklamları:** Program, kurs, atölye, webinar kaydı
  3. **İşe alım reklamları:** Ekip ilanları (Digience Akademi vb.)
- **Ses:** Enerjik, net, girişimci dili. Somut rakam, gerçek sonuç, dürüst beklenti.
  Kurumsal broşür dili yok, abartı yok (Türkiye Modu Bölüm 4 yasaklı liste geçerli).

> **TODO (kalibrasyon):** Ekibin en iyi performans veren 2-3 reklam senaryosu bu dosyaya
> "Örnek Senaryolar" başlığıyla eklenince ses tonu bu örneklere göre ayarlanacak.

---

## 2. CTA Mimarisi (SKILL.md "tek CTA" kuralının yerine geçer)

**Temel kural:** Tek **eylem**, birden çok **an.** CTA her seferinde aynı eylemi ister
(aynı link, aynı buton). İki farklı eylem ("forma git" + "DM at") asla aynı reklamda olmaz.
Değişen sadece CTA'nın söyleniş biçimi ve arkasındaki ikna ilkesidir.

### 2.1 Süreye göre CTA yerleşimi

| Reklam süresi | CTA sayısı | Yerleşim |
|---------------|-----------|----------|
| 60 sn'ye kadar | 2 | **Erken CTA** (hook bittikten sonra, en geç 20. saniye) + **Final CTA** |
| 60 sn-2 dk | 3 | Erken CTA (en geç 20. sn) + **Orta CTA** (yaklaşık ortada) + Final CTA |
| 2 dk üzeri (mini VSL, lansman videosu) | 4+ | Erken CTA (en geç 20. sn) + her 60-90 saniyede bir hatırlatma + Final CTA (son bölümde 2 kez) |

### 2.2 Her CTA'nın görevi farklıdır

- **Erken CTA (izin CTA'sı):** Kısa ve baskısız. Hemen karar vermiş olanı kaybetmemek için.
  "Link aşağıda, izlerken açık dursun." / "Kendini tanıdıysan başvuru linki açıklamada."
- **Orta CTA (gerekçe CTA'sı):** Az önce verilen bilgiye bağlanır. "Bunu zaten yapıyorsan
  seni arıyoruz, link açıklamada."
- **Final CTA (karar CTA'sı):** Kıtlık + süre + net eylem. Gerçek bir son tarih ve kontenjan
  varsa burada söylenir. "Kontenjan 40 kişi, kayıtlar pazar 23.59'da kapanıyor. Linke tıkla."

### 2.3 Görsel kural
CTA anlarında ekranda **aynı CTA sticker'ı / yazısı** görünür (örn. "BAŞVURU LİNKİ AŞAĞIDA ↓").
Final CTA'da sticker son saniyeye kadar ekranda kalır. Ses kapalı izleyen her CTA'yı okuyabilmeli.

### 2.4 Senaryo formatı (bu müşteri için)
```
[HOOK | 0-3 sn]
[BRIDGE | 3-x sn]
[CTA 1: ERKEN | en geç 20. sn]
[BODY 1]
[CTA 2: ORTA | sadece 60 sn üzeri]
[BODY 2]
[CTA 3: FİNAL | son 8-12 sn]
```
Her bloğun yanına kullanılan ikna ilkesi etiketlenir: `[CIALDINI: Kıtlık]`. Bu etiketler
ekip içi içindir; prompter metninden çıkarılır.

---

## 3. Cialdini'nin İkna İlkeleri (her reklamda zorunlu)

Ayrıntılı tanım ve örnekler: `../frameworks.md` Bölüm 12. Bu müşteri için kurallar:

- Her reklamda **en az 4 ilke** kullanılır ve senaryoda etiketlenir.
- Strateji planına "Cialdini Haritası" maddesi eklenir: hangi ilke, hangi saniyede, nasıl.
- **Kıtlık ve aciliyet gerçek olmalı.** Gerçek kontenjan, gerçek son tarih. Sahte geri sayım
  ve "son 3 kişi" yalanı Türk reklam hukukunda aldatıcı uygulamadır ve markaya güveni yakar.
- **Sosyal kanıt doğrulanabilir olmalı.** Öğrenci sayısı, mezun sonucu, takipçi sayısı
  kullanıcıdan alınır; yoksa `[X]` yer tutucusu konur. Uydurma rakam yazılmaz.
- **Otorite gerçek unvanla.** Türkiye Modu Bölüm 7.3 (yanıltıcı unvan yasağı).

### İlkelerin reklam türlerine göre öncelikli kullanımı

| Reklam türü | Öncelikli ilkeler |
|-------------|-------------------|
| Ön lansman / bekleme listesi | Karşılıklılık (ücretsiz değer), Tutarlılık (küçük evet: listeye katıl), Birlik |
| Kayıt açılışı | Sosyal kanıt, Otorite, Kıtlık (kontenjan) |
| Kapanış / son gün | Kıtlık (süre), Tutarlılık ("listeye katılmıştın"), Sosyal kanıt (kaç kişi katıldı) |
| Eğitim satışı (evergreen) | Otorite, Sosyal kanıt, Karşılıklılık |
| İşe alım | Kıtlık (pozisyon sayısı), Sempati (ekip içi), Tutarlılık (mikro evet + başvuru görevi), Karşılıklılık (videoda değer ver), Otorite/Sosyal kanıt (ekibin ölçeği) |

---

## 4. Lansman Reklamı Kalıpları

**Ön lansman (bekleme listesi):** Hook → değer (ücretsiz ipucu/mini ders) → Erken CTA
(listeye katıl) → neden şimdi → Final CTA. Teklifin fiyatı söylenmez; merak ve değer satılır.

**Kayıt açılışı:** Hook (sonuç veya merak) → Erken CTA → program ne veriyor (somut) → kanıt →
Orta CTA → kontenjan/süre → Final CTA.

**Kapanış (son 24-48 saat):** Hook doğrudan süre ile ("Kayıtlar bu gece 23.59'da kapanıyor.")
→ Erken CTA → kaç kişi katıldı → en sık sorulan itiraz cevabı → Final CTA.

**Eğitim reklamlarında Türkiye uyarısı:** Gelir vaadi ("ayda X TL kazan") Meta ve Reklam Kurulu
açısından risklidir. Gerçek ve belgeli öğrenci sonuçlarını, "sonuçlar kişiye göre değişir"
çerçevesiyle kullan (Türkiye Modu Bölüm 6.2).

---

## 5. İşe Alım Reklamları (Digience Akademi ve ekip ilanları)

Genel format: `../ad-formats.md` Format 9. Bu müşteri için ek kurallar:

- **Konuşmacı:** İlgili ekibin lideri veya ekipten biri. Gerçek ofis/çalışma ortamı.
- **Dürüst tempo:** İş yükü ve tempo açıkça söylenir (örn. "günde 6 video"). Bu, %99 Repel
  ilkesinin işe alım karşılığıdır: uygun olmayan aday başvurmaz, değerlendirme yükü azalır.
- **Başvuru görevi (Tutarlılık ilkesi):** Başvuruda küçük bir zihinsel yatırım istenir
  ("en iyi 3 işin ve neden tuttuğunu bir cümleyle yaz"). Ciddi adayı ayırır.
- **Tek eylem:** Başvuru formu/linki. CTA mimarisi (Bölüm 2) geçerli.
- **Uyum:** Meta'da "İstihdam" özel reklam kategorisi; yaş, cinsiyet, medeni durum şartı yok;
  başvuru formunda KVKK aday aydınlatma metni.

---

## 6. Yayınlanan Reklamlar Kaydı

| Tarih | Reklam | Tür | Durum / Sonuç |
|-------|--------|-----|---------------|
| 2026-11 | Digience Akademi: Sosyal Medya Video Editörü ilanı | İşe alım | Yazıldı, sonuç bekleniyor |
