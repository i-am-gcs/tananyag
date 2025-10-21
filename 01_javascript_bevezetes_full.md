# JavaScript bevezetés

A JavaScript az egyik legfontosabb nyelv, amit webfejlesztéshez használunk.  
Ha megnyitsz egy modern weboldalt, ott biztosan fut valamilyen JavaScript kód – ez az, ami életet visz az oldalba.  

A **HTML** adja a tartalmat, a **CSS** az arculatot, a **JavaScript** pedig a működést.  
Vagyis: **a JavaScript teszi interaktívvá az internetet.**

---

## Mi az a JavaScript?

A JavaScript egy magas szintű, dinamikus, többféle programozási stílust támogató nyelv, amit elsősorban a **weboldalak működtetésére** fejlesztettek.  
Ma már nemcsak a böngészőben, hanem a szervereken és más platformokon is fut.

### Röviden: mire használjuk?

- Gombokra, űrlapokra, menükre reagáló interaktív elemekhez  
- Webes alkalmazások logikájához (pl. kosár, chat, kereső)  
- Adatok lekérésére és feldolgozására (API-k, JSON adatok)  
- Mobil- és asztali appokhoz (React Native, Electron)  
- Szerveroldali programozáshoz (Node.js segítségével)

**Analógia:**  
A JavaScript olyan, mint az agy a weboldal testében – nélküle az oldal nem tudna reagálni semmire.

---

## Rövid története

A JavaScriptet **Brendan Eich** hozta létre 1995-ben, a Netscape cégnél.  
Az eredeti célja az volt, hogy a weboldalak ne csak statikus tartalmat mutassanak, hanem dinamikusan reagáljanak a felhasználókra.

Először **Mocha**, majd **LiveScript** volt a neve, végül marketing okból nevezték át **JavaScriptre**.  
A név megtévesztő, mert **a Java és a JavaScript két teljesen különböző nyelv** – csupán a szintaxisuk hasonlít.

### Fontosabb mérföldkövek:

| Év | Fejlemény |
|----|------------|
| 1995 | Az első verzió megjelenése (Netscape Navigator böngészőben) |
| 1997 | Szabványosítás ECMAScript néven |
| 2009 | Node.js megjelenése – JavaScript a szerveren is fut |
| 2015 | ES6 (ECMAScript 2015) – modern nyelvi elemek, mint let/const, arrow function, class stb. |

A mai JavaScript már egy fejlett, gyors és sokoldalú nyelv, amit a legtöbb fejlesztő napi szinten használ.

---

## Hol fut a JavaScript?

A JavaScriptet eredetileg a böngészőkhöz tervezték, de ma már **bármilyen környezetben futtatható**, ahol van JavaScript motor.

### Böngészőben
A legklasszikusabb helye. A kódot közvetlenül a HTML fájlba is beillesztheted:

```html
<!DOCTYPE html>
<html>
  <body>
    <h1 id="title">Hello!</h1>

    <script>
      document.getElementById("title").innerText = "Szia JavaScript!";
    </script>
  </body>
</html>
```

Ez a kis program az oldal betöltésekor átírja a cím szövegét.  

👉 Itt a JavaScript a HTML dokumentumot kezeli – ezt hívjuk **DOM manipulációnak**.

### Szerveren – Node.js
A **Node.js** segítségével JavaScriptet futtathatsz böngésző nélkül, szerveroldalon is:

```js
// hello.js
console.log("Hello from Node.js!");
```

Terminálban futtatva:
```
node hello.js
```
Kimenet:
```
Hello from Node.js!
```

Ez azt jelenti, hogy **ugyanazzal a nyelvvel** írhatod meg a frontend és a backend logikát is.

---

## A JavaScript fő jellemzői

### 1. Dinamikus típusosság
A változók típusát nem kell előre megadni – a nyelv futásidőben dönti el.

```js
let data = 42;       // number
data = "Hello";      // string – típus megváltozott
```

Ez nagyon rugalmas, de figyelni kell, mert a típusváltások hibákat okozhatnak.

### 2. Értelmezett nyelv
A JavaScript kódot **nem fordítjuk le előre**, mint pl. a C-t vagy Javát.  
A motor (pl. Chrome-ban a V8) **sorban olvassa és futtatja** az utasításokat.

### 3. Egy szálon fut
A JavaScript egyszerre csak egy dolgot végez, de az **aszinkron működés** miatt mégis úgy tűnik, mintha párhuzamos lenne.  
Erről majd az aszinkron fejezetben lesz szó (Promise, async/await).

### 4. Objektumorientált és funkcionális is
Nem muszáj kizárólag osztályokat használni – a JavaScript támogatja a funkcionális stílust is.  
Sokféleképp lehet benne ugyanazt a problémát megoldani.

### 5. Platformfüggetlen
A JavaScript mindenhol működik, ahol van JavaScript motor – böngészőben, szerveren, sőt beágyazott eszközökön is.

---

## Hogyan kezdj neki a gyakorlásnak?

### 1. Konzol (gyors teszteléshez)
Nyisd meg a böngészőben a **fejlesztői eszközöket** (F12), majd válaszd a **Console** fület.  
Ide bármilyen kódot beírhatsz, és azonnal látod az eredményt:

```js
console.log("Hello, JavaScript!");
```

### 2. Saját fájl (HTML + JS)
Készíts egy `index.html` fájlt, és illeszd be:

```html
<!DOCTYPE html>
<html>
  <body>
    <script>
      alert("Hello JavaScript!");
    </script>
  </body>
</html>
```

Mentés után nyisd meg böngészőben – az első saját programod máris működik 🎉

### 3. Fejlesztői környezet
Komolyabb projektekhez érdemes a **Visual Studio Code**-ot használni:  
ingyenes, gyors, és rengeteg bővítményt kínál JavaScripthez.

---

## Alap fogalmak, amiket érdemes megjegyezni

### Utasítások (statements)
Minden sor egy utasítás. Általában pontosvessző (`;`) zárja.

```js
let name = "Anna";
console.log(name);
```

### Megjegyzések (kommentek)
A megjegyzések nem futnak le, csak neked segítenek olvasni a kódot.

```js
// Ez egy egysoros megjegyzés

/* Ez pedig egy
   több soros megjegyzés */
```

### Kiíratás
A `console.log()` segítségével láthatod, mi történik a programodban:

```js
console.log("Üzenet a konzolra");
```

---

## Miért érdemes JavaScriptet tanulni?

- Szinte **minden modern weboldal** JavaScriptet használ.  
- Már **néhány sor kóddal** is látványos eredményt kapsz.  
- Egy nyelv elég lehet **frontendre és backendre** is.  
- Hatalmas közösség és ingyenes tananyagok segítenek a fejlődésben.  
- Nagyon keresett tudás a munkaerőpiacon.

A JavaScript jó belépő a programozás világába: látványos, hasznos és logikát fejleszt.

---

## Összefoglalva

A JavaScript a web egyik alapköve.  
Segítségével dinamikus, reagáló, interaktív alkalmazásokat hozhatsz létre, amelyek életet visznek az internetbe.

Ha megérted az alapokat, egy teljes világ nyílik meg előtted – a webfejlesztés, az API-k, és a modern appok világa.

A következő fejezetben megtanulod, hogyan tároljunk és kezeljünk adatokat – vagyis jönnek a **változók és konstansok**.
