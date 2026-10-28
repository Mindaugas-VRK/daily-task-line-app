# Daily Task Line – įdiegimas

Programėlė veikia naršyklėje ir įsidiegia kaip programa kompiuteryje ir telefone. Kiekvienas workspace saugomas atskirai: **tik šiame įrenginyje** arba **savo Google paskyros Drive** (pvz., Personal → asmeninis Gmail, Softeta → darbo paskyra).

Viską reikia padaryti vieną kartą, užtrunka apie 15 minučių.

---

## 1. Įkelkite programėlę į internetą (GitHub Pages, nemokamai)

1. Prisijunkite arba užsiregistruokite <https://github.com>.
2. Spauskite **+ → New repository**. Pavadinimas, pvz., `tasks`, pasirinkite **Public** ir spauskite **Create repository**.
3. Spauskite **uploading an existing file** ir nutempkite visus šio aplanko failus (`index.html`, `config.js`, `sw.js`, `manifest.webmanifest` ir visus `.png`). Tada **Commit changes**.
4. **Settings → Pages**. Prie **Branch** pasirinkite `main` ir `/ (root)`, tada **Save**.
5. Po minutės ar dviejų viršuje pasirodys nuoroda, pvz., `https://jusu-vardas.github.io/tasks/`. Tai jūsų programėlės adresas.

Saugumas: viešas yra tik programos kodas. Užduotys į GitHub nepatenka, jos lieka jūsų įrenginyje arba jūsų Google Drive.

## 2. Gaukite Google prisijungimo raktą (Client ID)

Darykite prisijungę prie **asmeninės** Google paskyros.

1. Atidarykite <https://console.cloud.google.com> ir sukurkite naują projektą (viršuje projekto pasirinkimas → **New project**), pvz., `Daily Task Line`.
2. **APIs & Services → Library**: suraskite **Google Drive API** ir spauskite **Enable**.
3. **Google Auth Platform** (arba **OAuth consent screen**) → **Get started**:
   - App name: `Daily Task Line`, support email: jūsų el. paštas;
   - Audience: **External**;
   - Contact: jūsų el. paštas → **Create**.
4. **Audience → Test users → Add users**: įrašykite **visas** paskyras, kurias jungsite (asmeninį Gmail ir darbo el. paštą).
5. **Data access → Add or remove scopes**: pažymėkite `.../auth/drive.file` („See, edit, create and delete only the specific Google Drive files you use with this app“) → **Update → Save**.
6. **Clients → Create client**:
   - Application type: **Web application**;
   - **Authorized JavaScript origins → Add URI**: `https://jusu-vardas.github.io` (be `/tasks` ir be `/` gale);
   - **Create**. Nukopijuokite **Client ID** (atrodo kaip `123…-abc….apps.googleusercontent.com`).
7. GitHub repozitorijoje atidarykite `config.js`, spauskite ✏️, įklijuokite Client ID tarp kabučių ir spauskite **Commit changes**:
   ```js
   googleClientId: "123…-abc….apps.googleusercontent.com",
   ```

Programėlė mato **tik tuos Drive failus, kuriuos pati sukūrė**, o ne visą jūsų Drive.

## 3. Įsidiekite

- **Kompiuteryje (Chrome arba Edge):** atidarykite nuorodą ir spauskite įdiegimo ikoną adreso juostoje arba **Install app** puslapio apačioje.
- **Mac Safari:** **File → Add to Dock**.
- **iPhone:** atidarykite nuorodą **Safari** → Share → **Add to Home Screen**.
- **Android:** Chrome → ⋮ → **Install app** (arba **Add to Home screen**).

## 4. Prijunkite workspace'us prie Google

1. Atidarykite **Personal** skirtuką → **Sync with Google Drive** → pasirinkite asmeninę paskyrą.
2. Atidarykite **Softeta** → **Sync with Google Drive** → pasirinkite darbo paskyrą.
3. Pirmą kartą Google parodys „Google hasn't verified this app“. Tai normalu, nes programėlę sukūrėte jūs: **Continue**, tada leiskite prieigą prie Drive failų.

Kiekvienas workspace Drive'e turi savo failą, pvz., `Daily Task Line – Personal.json`. Ranka jo netaisykite.

**Naujame įrenginyje:** atidarykite programėlę, pasirinkite skirtuką ir spauskite **Sync with Google Drive** su ta pačia paskyra. Užduotys atsiras. Workspace'ą, kurį sukūrėte patys, pirma sukurkite tokiu pačiu pavadinimu, tada prijunkite: failas susiejamas pagal workspace'o pavadinimą.

## Ką verta žinoti

- **Prisijungimas galioja apie valandą.** Po to viršuje atsiras **Reconnect**: vienas paspaudimas. Pakeitimai per tą laiką neprarandami, jie išsisaugo įrenginyje ir nusiunčiami prisijungus.
- **Paskyros nesusimaišo.** Jei jungdamiesi pasirinksite ne tą paskyrą, programėlė to neleis. Paskyrą galima pakeisti tik per **Settings → Switch account**.
- **Darbo paskyra:** jei Softeta Google administratorius blokuoja nepatvirtintas programėles, Softeta workspace'ui pasirinkite **This device only** (Settings) arba paprašykite administratoriaus leidimo.
- **Priminimai:** puslapio apačioje **Turn on reminder notifications**. Kompiuteryje ir Android veikia, kol programėlė atidaryta arba fone. iPhone pranešimai iš tokių programėlių riboti.
- **Atnaujinimas:** įkelkite naujus failus į GitHub. Programėlė atsinaujins kitą kartą ją atidarius.
