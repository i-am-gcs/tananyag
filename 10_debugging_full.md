# Hibakeresés és Debugging a JavaScriptben (VS Code használattal)

A hibakeresés (angolul **debugging**) a programozás egyik legfontosabb része.  
A hibák **nem ellenségek**, hanem **jelzések**, hogy valami nem úgy működik, ahogy vártad.  
Ha megtanulsz jól hibát keresni, sokkal gyorsabban fejlődsz fejlesztőként.

Ebben a fejezetben megnézzük, hogyan találhatod meg és javíthatod a hibákat **JavaScriptben**, különösen **VS Code-ban dolgozva**.

---

## Mi az a hiba (bug)?

A „bug” (hiba) egy olyan rész a kódban, ami miatt a program **nem a várt módon viselkedik**.  
Ez lehet valami apróság — például elírás — vagy logikai hiba, ami miatt a program rossz eredményt ad.

**Példa:**

```js
let szam = 5;

if (szam = 10) {   // ❌ Hiba: egyenlőség helyett értékadás!
  console.log("A szám 10");
}
```

Ez a kód mindig „A szám 10”-et ír ki, mert az `=` nem összehasonlítás, hanem értékadás.

---

## A hibák típusai

A hibák három fő kategóriába sorolhatók:

| Hibatípus | Jelentés | Példa |
|------------|-----------|--------|
| **Szintaktikai hiba (Syntax Error)** | A JavaScript nem érti a kódot | `if (x > 5 {` |
| **Futásidejű hiba (Runtime Error)** | A program fut, de hibába ütközik | `console.log(abc)` (nem létező változó) |
| **Logikai hiba (Logic Error)** | A program lefut, de rossz eredményt ad | Hibás számítás, rossz feltétel |

---

## 1️⃣ Console.log() – a fejlesztő legjobb barátja

A legegyszerűbb módja annak, hogy lásd, mi történik a kódban: a **console.log()**.

Ez kiírja a konzolra, amit átadsz neki, így nyomon követheted a változók értékeit.

**Példa:**

```js
let a = 10;
let b = 5;

console.log("A értéke:", a);
console.log("B értéke:", b);
console.log("Összeg:", a + b);
```

VS Code-ban a kimenetet a **Terminal** fülön látod, ha Node.js-sel futtatod a fájlt:

```
node script.js
```

Eredmény:
```
A értéke: 10
B értéke: 5
Összeg: 15
```

**Tipp:** Használj beszédes üzeneteket, hogy pontosan tudd, melyik rész futott le.

---

## 2️⃣ Console.error(), Console.warn()

Ezek segítségével **különböző típusú üzeneteket** is megkülönböztethetsz a konzolon.

```js
console.error("Hiba történt!");
console.warn("Figyelmeztetés: ez nem biztos, hogy helyes.");
```

A `console.error` pirossal, a `console.warn` sárgával jelenik meg – így könnyebben átlátható a kimenet.

---

## 3️⃣ debugger – a beépített megállító pont

A JavaScript rendelkezik egy **beépített parancssal**, amivel a kód futását megállíthatod:

```js
let x = 10;
let y = 5;

debugger; // 🧩 a program itt megáll, és belép a debugger módba

let eredmeny = x + y;
console.log(eredmeny);
```

Ha a VS Code debuggerével futtatod a kódot, a program **itt megáll**, és láthatod a változók aktuális értékeit.

---

## 4️⃣ Hibakeresés VS Code-ban (Debugging mód)

A **Visual Studio Code** egy beépített debuggerrel rendelkezik, ami segít lépésről lépésre futtatni a programot.

### 🪄 Lépések:

1. **Nyisd meg a projekted VS Code-ban.**  
2. A bal oldali oldalsávban kattints a „Run and Debug” ikonra (vagy nyomd meg a `Ctrl + Shift + D` billentyűt).  
3. Ha még nincs konfigurálva, válaszd: **„Run and Debug” → „Node.js”**.  
4. Helyezz el egy **piros pontot** a kód sorának bal szélén – ez lesz a **breakpoint** (megszakítási pont).  
5. Nyomd meg az **F5** gombot (vagy a „Start Debugging” zöld nyilat).  

A program **megáll a breakpointnál**, és a felső debug eszköztárban láthatod a vezérlőket.

---

## 5️⃣ A Debugger eszköztára

Amikor a kód megáll, több lehetőséged is van:

| Gomb | Funkció | Mit csinál |
|------|----------|-------------|
| ▶️ **Continue (F5)** | Folytatja a programot a következő breakpointig |
| ⏭️ **Step Over (F10)** | Lefuttatja az aktuális sort, de nem lép be a függvénybe |
| ⤵️ **Step Into (F11)** | Belép a függvénybe, hogy belül is megnézd a működést |
| ⏹️ **Stop (Shift+F5)** | Leállítja a futást |
| ↩️ **Restart (Ctrl+Shift+F5)** | Újraindítja a programot |

---

## 6️⃣ Változók figyelése (Watch, Variables, Call Stack)

A debugger **bal oldali paneljén** három fontos eszköz segít megérteni a kód működését:

| Panel | Mit mutat |
|--------|------------|
| **Variables** | A pillanatnyi változók értékeit |
| **Watch** | Saját magad által megadott kifejezések, amiket figyelni szeretnél |
| **Call Stack** | Hívási lánc – megmutatja, melyik függvényből hívtál meg egy másikat |

**Példa:**
```js
function osszead(a, b) {
  return a + b;
}

function futtas() {
  let eredmeny = osszead(5, 7);
  console.log("Eredmény:", eredmeny);
}

futtas();
```

A **Call Stack** így néz ki, amikor a program az `osszead` függvényben áll:
```
osszead()
futtas()
```

---

## 7️⃣ Tipikus hibák és azok felismerése VS Code-ban

### Szintaktikai hiba:
A VS Code azonnal piros hullámos aláhúzással jelzi:
```js
if (x > 5 { // hiányzó zárójel
```

### Futásidejű hiba:
A terminálban jelenik meg piros hibaüzenet formájában:
```
ReferenceError: y is not defined
```

### Logikai hiba:
Nem kapsz hibaüzenetet, de az eredmény nem az, amit vártál.  
Ebben az esetben **console.log()** vagy a **debugger** segít megtalálni a gondot.

---

## 8️⃣ try...catch – hibakezelés a kódban

A JavaScript lehetőséget ad a hibák **elkapására és kezelésére**.

```js
try {
  let eredmeny = 10 / 0;
  console.log(eredmeny);
  let x = y + 5; // hiba
} catch (hiba) {
  console.error("Hiba történt:", hiba.message);
} finally {
  console.log("A kód ide mindig lefut.");
}
```

A `finally` blokk mindig lefut, még akkor is, ha hiba történt.

---

## 9️⃣ breakpoints VS Code-ban – gyakorlati példa

```js
function szamol(a, b) {
  let osszeg = a + b;
  let kulonbseg = a - b;
  let szorzat = a * b;
  return { osszeg, kulonbseg, szorzat };
}

let eredmeny = szamol(10, 5);
console.log(eredmeny);
```

### Debug lépések:

1. Tedd a kurzort a `let osszeg = a + b;` sor elejére, és kattints a bal margóra → megjelenik egy **piros pont**.  
2. Nyomd meg az **F5** gombot a futtatáshoz.  
3. A program **megáll** a megadott sornál.  
4. Nézd meg a „Variables” panelen a `a` és `b` értékét.  
5. Lépj tovább `Step Over`-rel, és figyeld, hogyan változnak a változók.  

---

## 🔍 Gyakori hibakeresési technikák

| Technika | Mikor használd |
|-----------|----------------|
| `console.log()` | Egyszerű gyors hibakereséshez |
| `debugger` | Ha meg szeretnéd állítani a kódot és belenézni |
| **Breakpoints** | Részletes, lépésenkénti hibakereséshez VS Code-ban |
| **Watch / Variables panel** | Változók figyelésére futás közben |
| **try...catch** | Hibák biztonságos kezelésére a kódban |

---

## 🧠 Tippek hibakereséshez

💡 Mindig olvasd el figyelmesen a hibaüzenetet – gyakran pontosan megmondja, mi a baj.  
💡 Ha valami `undefined`, logold ki a változót, mielőtt használod.  
💡 Ne keresd megérzésből – **izoláld** a hibát kis kódrészletekre.  
💡 Használd a `debugger` kulcsszót, hogy megállítsd a futást a problémás résznél.  
💡 Hibátlan kód nincs – de gyors hibakeresés igen. 😉

---

## Összefoglalás

- A hibák elkerülhetetlenek, de megtanulhatók gyorsan kezelni.  
- A `console` eszközei segítenek a diagnosztikában.  
- A `debugger` és a **VS Code Debugger** lehetővé teszi a lépésenkénti vizsgálatot.  
- A `try...catch` szerkezet biztonságossá teszi a futást.  
- A jó hibakereső fejlesztő **türelmes és kíváncsi** – minden hiba egy tanulási lehetőség.  

---

## ✅ Mini gyakorlófeladat

1. Hozz létre egy `debug_practice.js` fájlt.  
2. Írd bele ezt a kódot:

```js
function osztas(a, b) {
  let eredmeny = a / b;
  console.log("Eredmény:", eredmeny);
}

osztas(10, 0);
```

3. Futtasd VS Code-ban, és nézd meg a hibát.  
4. Javítsd ki úgy, hogy ne legyen hiba, például:

```js
function osztas(a, b) {
  if (b === 0) {
    console.error("Nem lehet nullával osztani!");
    return;
  }
  console.log("Eredmény:", a / b);
}
```

Gratulálok 🎉 — ezzel lezártad a **JavaScript alapok** teljes elméleti modulját!  
Most már magabiztosan tudsz hibát keresni és megérteni, mi történik a kódodban.
