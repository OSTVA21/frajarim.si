# Povezava ocen s Firebase (frajarim.si)

Trajalo bo približno 10 minut. Račun in Firebase paket Spark sta brezplačna.

## 1. Ustvari projekt
1. Odpri https://console.firebase.google.com in se prijavi z Google računom.
2. Klikni **Create a project** (Ustvari projekt), ime npr. `frajarim`.
3. Google Analytics lahko izklopiš. Klikni **Create project**.

## 2. Vključi bazo Firestore
1. V levem meniju: **Build > Firestore Database > Create database**.
2. Izberi lokacijo **eur3 (europe-west)** ali drugo evropsko.
3. Izberi **Start in production mode** in potrdi.

## 3. Prilepi varnostna pravila
1. V Firestore odpri zavihek **Rules**.
2. Izbriši vse in prilepi celotno vsebino datoteke `firestore.rules`.
3. Klikni **Publish**.

Pravila poskrbijo, da lahko obiskovalci ocene samo preberejo in dodajo (ne morejo jih spreminjati ali brisati), e-pošte ocenjevalcev pa nihče razen vas ne more prebrati.

## 4. Pridobi nastavitve za stran
1. Zgoraj levo klikni zobnik **Project settings**.
2. Pod **Your apps** klikni ikono **</>** (Web), vzdevek npr. `frajarim-web`. Hostinga ne vključuj.
3. Prikaže se `firebaseConfig = { apiKey: ..., authDomain: ..., ... }`.
4. Pošlji mi te vrednosti (ali jih sam prepiši v `index.html` v blok `FIREBASE_CONFIG`, ki ga najdeš z iskanjem `VSTAVI`).

Te vrednosti niso skrivnost. Zaščito dajejo pravila iz 3. koraka.

## 5. Naloži stran na GitHub
Zamenjaj `index.html` v repozitoriju z novo datoteko. Po minuti ali dveh je stran posodobljena.

## Kje vidim e-pošte ocenjevalcev?
Firebase konzola > Firestore Database > zbirka **reviewerEmails**. Vsaka vrstica ima e-pošto, ime in oceno. Poleg tega vsaka nova ocena pride tudi na ostva@outlook.com.

## Kako izbrišem neprimerno oceno?
Firebase konzola > Firestore Database > zbirka **reviews** > ob dokumentu kliknite tri pike > **Delete document**.

## Pri prvi oceni
Formsubmit lahko pri prvi poslani oceni pošlje na ostva@outlook.com e-pošto za potrditev. Klikni povezavo v njej. Če si prejšnji obrazec že potrdil, tega ne bo.
