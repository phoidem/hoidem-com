# hoidem.com — OAuth branding for Songmirror

Dwie publiczne strony, żeby Google Auth Platform mógł **App veröffentlichen**
(bez tego OAuth zostaje w Test i token pada co 7 dni).

- Pusta strona główna: `https://hoidem.com/` (bez linków)
- OAuth Startseite: `https://hoidem.com/songmirror/`
- OAuth Datenschutz: `https://hoidem.com/songmirror/datenschutz.html`
- Repo: https://github.com/phoidem/hoidem-com
- Pages: GitHub Settings → Pages → Branch `main` / root (potem Enforce HTTPS)

## Dlaczego goneo mówi „keine aktiven Pakete”

To **nie** znaczy, że domena wygasła.

| | |
|--|--|
| Pakiet goneo (web + E-Mail Plus) | wypowiedziany, koniec **30.07.2026** — panel Kundencenter jest martwy |
| Rejestracja `hoidem.com` | do **19.02.2027** (Ascio) |
| Nameservery dziś | nadal `ns1.goneo.de` / `ns2.goneo.de` (parking) |

Panel goneo wymaga aktywnego pakietu. Po wypowiedzeniu logowanie jest celowo zablokowane. DNS nadal trzyma goneo, ale **Ty nie masz już GUI**, żeby zmienić A/CNAME.

W kwietniu 2026 prosiłeś o NS Cloudflare (`jessica.ns.cloudflare.com`, `trey.ns.cloudflare.com`). W DNS tego **nie ma** — goneo nie przełączyło delegacji.

## Co zrobić z DNS (goneo nie wejdzie)

1. Wejdź na [Cloudflare](https://dash.cloudflare.com) (to konto z kwietnia, te dwa NS są unikalne).
2. Dodaj domenę `hoidem.com`, jeśli jej tam nie ma. Cloudflare pokaże te same NS.
3. Rekordy (szary cloud / DNS only, nie pomarańczowy proxy — GitHub Pages tego nie lubi):

- **A** `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
- **AAAA** `@` → `2606:50c0:8000::153` … `8003::153`
- **CNAME** `www` → `phoidem.github.io`

4. Mail do **vertrag@goneo.de** (konto 107057), krótko:

```
Paket E-Mail Plus / Webserver ist seit 30.07.2026 gekündigt, Kundencenter:
„keine aktiven Pakete“. Domain hoidem.com läuft bis 19.02.2027.

Bitte Nameserver umstellen auf:
jessica.ns.cloudflare.com
trey.ns.cloudflare.com

Bitte Auth-Code (EPP) schicken, falls die NS-Änderung nicht mehr möglich ist.
```

Bez tego kroku GitHub Pages nie zobaczy `hoidem.com`.

## Google, gdy `https://hoidem.com/` już otwiera te strony

1. [Search Console](https://search.google.com/search-console) — domena `hoidem.com`, TXT w **Cloudflare**, konto `phoidem@gmail.com`.
2. Cloud → Branding: dwa URL-e powyżej → Speichern.
3. Zielgruppe → Autorisierte Domains → `hoidem.com` → App veröffentlichen.
4. SongMirror → YouTube Music → **Erneut verbinden**.
