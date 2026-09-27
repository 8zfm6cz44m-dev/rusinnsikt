# Rusinnsikt

Et nøytralt, faktabasert oppslagsverk om rusmidler og risiko for iOS og Android.
Fakta, nødhjelp og søk ligger i appen – uten internett, uten konto og uten sporing.

- Support og vanlige spørsmål: https://devlyn.no/rusinnsikt/
- Personvernerklæring: https://devlyn.no/rusinnsikt/personvern/
- Kontakt: info@rusinnsikt.no

## Hvorfor koden er åpen

Appen lover at ingenting sendes noe sted, at ingen konto finnes og at den ikke lagrer hva du
har lest eller søkt på. Den beste måten å stå inne for et slikt løfte på er å la hvem som helst
lese koden. Se `PERSONVERN_AUDIT.md` for gjennomgangen og `scripts/personvern-sjekk.sh` for
kontrollen som kjøres før hver utgivelse.

Kort fortalt:

- Ingen nettverkskall. Android-manifestet ber ikke engang om `INTERNET`.
- Ingen tredjepartsbiblioteker (iOS: null Swift-pakker; Android: kun AndroidX/Compose).
- Én lokal innstilling: om velkomstskjermen er sett. Unntatt fra sky-backup.
- Innholdet skjules i app-veksleren.

## Struktur

| Mappe | Innhold |
|---|---|
| `Rusinnsikt/` | iOS-appen (SwiftUI) |
| `RusinnsiktTests/` | iOS-tester (Cmd+U i Xcode) |
| `android/` | Android-appen (Kotlin/Jetpack Compose) |
| `Rusinnsikt/RusFaktaApp/Resources/Substances.json` | Alt innhold. Skal alltid være byte-identisk med `android/app/src/main/assets/substances.json` |
| `docs/` | Support- og personverntekster, nettsidene på devlyn.no |
| `scripts/personvern-sjekk.sh` | Personvern-kontroll som må gi alle PASS før utgivelse |

Bygg: åpne `Rusinnsikt.xcodeproj` i Xcode (sett ditt eget utviklingsteam under Signing), eller
`android/` i Android Studio. Se `README_BUILD_GUIDE.md`.

## Innhold og kilder

Substansinnholdet er skrevet om og forkortet fra offentlige norske kilder – RUSinfo (Oslo kommune),
Helsedirektoratet, Folkehelseinstituttet, Direktoratet for medisinske produkter, Giftinformasjonen /
Helsebiblioteket, Kripos og Oslo universitetssykehus – supplert med internasjonale regulatoriske og
fagfellevurderte kilder. Hvert stoff oppgir sine kilder i feltet `sourceNote`. Innholdet kontrolleres
jevnlig mot kildene. Rådene om risikoreduksjon inneholder aldri doser eller bruksanvisninger; det
sikres av tester på begge plattformer.

Appen oppfordrer ikke til bruk og erstatter ikke medisinsk vurdering eller akutthjelp.
Ved mistanke om overdose: ring 113.

Rusinnsikt er et uavhengig prosjekt og er ikke tilknyttet rusinfo.no, rusopplysningen.no,
Oslo kommune eller Helsedirektoratet.

## Lisens

Koden er utgitt under MIT-lisensen (se `LICENSE`). Utgiver: Devlyn IT.
