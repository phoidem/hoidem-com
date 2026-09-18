# hoidem.com — OAuth branding for Songmirror

Dwie publiczne strony (Startseite + Datenschutz), żeby Google Auth Platform
mógł **App veröffentlichen**. Bez tego OAuth zostaje w Test i token pada co 7 dni.

Hosting: **GitHub Pages** (darmowy HTTPS). DNS dziś trzyma goneo-parking
(`notavailable.goneo.de`), HTTPS na apex nie działa.

## URLe po DNS

- Startseite: `https://hoidem.com/`
- Datenschutzerklärung: `https://hoidem.com/datenschutz.html`

## DNS w goneo (zamiast parkingu)

Usuń A/CNAME parkingu na `@` i `www`. Ustaw:

**A** `@` →

- `185.199.108.153`
- `185.199.109.153`
- `185.199.110.153`
- `185.199.111.153`

**AAAA** `@` →

- `2606:50c0:8000::153`
- `2606:50c0:8001::153`
- `2606:50c0:8002::153`
- `2606:50c0:8003::153`

**CNAME** `www` → `phoidem.github.io`

TTL krótki (300) na czas zmiany.

## Google po tym, jak HTTPS odpowiada 200

1. [Search Console](https://search.google.com/search-console) — właściwość **Domena** `hoidem.com`, DNS TXT z kreatora, w goneo dodać TXT, Verify. Konto: `phoidem@gmail.com` (to samo co projekt Cloud).
2. Auth Platform → **Branding**: Startseite i Datenschutz jak wyżej. **Speichern**.
3. **Zielgruppe** → **Autorisierte Domains** → `hoidem.com` → **App veröffentlichen**.
4. SongMirror → YouTube Music → **Erneut verbinden** (stary token z Test i tak padnie po 7 dniach).
