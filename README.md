# HAUNTED HOUSE — Cursed Poker

Tek dosyalık, çevrimdışı çalışan gotik poker roguelike. Firebase Hosting üzerinde statik site olarak yayınlanabilir; backend veya veritabanı gerekmez. Kayıtlar tarayıcının `localStorage` alanında tutulur.

## İçerik

- `index.html` — oyunun tamamı (HTML + CSS + JS + SVG, harici bağımlılık yok)
- `firebase.json` — Firebase Hosting yapılandırması
- `.gitignore` — Firebase/Git gereksiz dosyaları

## Yerelde çalıştırma

Dosyaya çift tıklayabilirsin ya da basit bir sunucuyla açabilirsin:

```bash
npx serve .
```

Ardından `http://localhost:3000` adresini aç.

## Firebase Hosting'e yayınlama

Ön koşul: Node.js 18+ ve Firebase CLI.

```bash
npm install -g firebase-tools
firebase login
cd haunted-house
firebase use --add      # Firebase projeni seç
firebase deploy --only hosting
```

Çıktıda Firebase sana `https://PROJE-ID.web.app` adresini verir.

## Özel domain bağlama

1. Firebase Console → **Hosting** → **Add custom domain**.
2. Domain sağlayıcısında istenen `A` / `CNAME` kayıtlarını ekle.
3. DNS yayılınca Firebase sertifikayı otomatik oluşturur.
4. `firebase.json` içindeki `rewrites` sayesinde tüm yollar `index.html`'e yönlenir.

## GitHub

```bash
git init
git add .
git commit -m "HAUNTED HOUSE — initial release"
git branch -M main
git remote add origin https://github.com/KULLANICI/haunted-house.git
git push -u origin main
```

Docker, npm build veya CI gerekmez. İstersen sonraki adımda `firebase deploy`'u GitHub Actions ile otomatikleştirebilirsin.

## Notlar

- Oyun adı ve tema: **HAUNTED HOUSE**.
- Eski `house-poker-v10.html` korunur; bu klasör yayın için temiz kopyadır.
- Günlük seed, jokerler ve başarımlar tarayıcıda saklanır. Firebase yalnızca statik dosyayı sunar.
- Rakip hedefi sabit eğri yerine; mevcut deste, jokerler ve yükseltmelerle 24 denemede üretilen tipik tur skoruna göre hesaplanır. Boss, bribe ve zorluk lanetleri bu hedefe eklenir.
