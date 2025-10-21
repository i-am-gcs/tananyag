# JavaScript adattípusok és típuskonverziók

A JavaScript egyik legérdekesebb tulajdonsága, hogy **nem kell előre megmondanod**, milyen típusú adatot tárolsz egy változóban.  
A nyelv **futás közben dönti el**, és akár útközben is megváltozhat.  

Ez nagyon kényelmes, de néha váratlan eredményekhez vezethet, ha nem figyelünk oda.  
Ebben a fejezetben megnézzük, **milyen típusok vannak**, hogyan működik a típusváltás (konverzió), és mire érdemes figyelni.

---

## Mik azok az adattípusok?

Az adattípus (vagy egyszerűen típus) azt mondja meg, **milyen jellegű adatot** tárol egy változó.  
Másként fogalmazva: mit tudsz vele csinálni — számolni, szöveget kiírni, logikai műveletet végezni stb.

Például:

```js
let szam = 42;          // number
let szoveg = "Hello";   // string
let logikai = true;     // boolean
```

---

## JavaScript alap típusai

A JavaScriptben két nagy kategória van:

1. **Primitív típusok** – egyszerű, egyetlen értéket tartalmaznak  
2. **Összetett (referencia) típusok** – több adatot vagy kapcsolatokat tárolnak

### Primitív típusok:

| Típus | Példa | Jelentés |
|--------|--------|----------|
| string | `"alma"` | szöveg |
| number | `42`, `3.14` | szám |
| boolean | `true` / `false` | logikai érték |
| undefined | – | nincs érték hozzárendelve |
| null | `null` | „üres” érték, szándékosan üres |
| symbol | `Symbol("id")` | egyedi azonosító |
| bigint | `123n` | nagyon nagy egész számokhoz |

### Összetett típusok:

| Típus | Példa | Jelentés |
|--------|--------|----------|
| object | `{ nev: "Anna", kor: 25 }` | kulcs–érték párok |
| array | `["alma", "körte", "banán"]` | lista, rendezett elemek |
| function | `function(){}` | újrafelhasználható kódrészlet |

---

## Szövegek (String)

A **string** típus szöveget tartalmaz. A szöveget idézőjelek közé kell tenni — lehetnek `'`, `"` vagy backtick (`` ` ``).

```js
let uzenet1 = "Hello";
let uzenet2 = 'Szia';
let uzenet3 = `Helló, ${uzenet1}!`; // template literal
```

**Példa – összefűzés:**
```js
let nev = "Anna";
let koszones = "Szia, " + nev + "!";
console.log(koszones); // Szia, Anna!
```

**Példa – template literal:**
```js
let kor = 25;
console.log(`Anna ${kor} éves.`); // Anna 25 éves.
```

**Tipp:** mindig használd a backtick-et (`` ` ``), ha változókat akarsz szövegbe illeszteni – sokkal olvashatóbb.

---

## Számok (Number)

A JavaScriptben **minden szám** ugyanahhoz a típushoz tartozik – akár egész, akár tizedes.

```js
let egesz = 10;
let tort = 3.14;
let negativ = -7;
```

Matematikai műveletek ugyanúgy működnek, mint más nyelvekben:

```js
let osszeg = 5 + 3;    // 8
let kulonbseg = 10 - 2; // 8
let szorzas = 4 * 2;   // 8
let osztas = 16 / 2;   // 8
```

### Különleges számértékek:

| Érték | Jelentés |
|--------|-----------|
| `Infinity` | végtelen |
| `-Infinity` | negatív végtelen |
| `NaN` | „Not a Number” – ha számítás értelmetlen |

**Példa:**
```js
console.log(10 / 0);  // Infinity
console.log(0 / 0);   // NaN
```

**Tipp:** ha `NaN`-t látsz, az általában azt jelenti, hogy nem szám típusú értékkel próbáltál műveletet végezni.

---

## Logikai értékek (Boolean)

A boolean két értéket vehet fel: `true` vagy `false`.  
Ez alapja az **elágazásoknak**, **vizsgálatoknak** és **feltételeknek**.

```js
let nagyobb = 10 > 5;  // true
let kisebb = 5 > 10;   // false
let egyenlo = 10 === 10; // true
```

A logikai operátorok:  
- `&&` – és (AND)  
- `||` – vagy (OR)  
- `!` – nem (NOT)

**Példa:**
```js
let felhasznaloBelepett = true;
let vanJogosultsag = false;

if (felhasznaloBelepett && vanJogosultsag) {
  console.log("Hozzáférés engedélyezve.");
} else {
  console.log("Nincs jogosultság.");
}
```

---

## Undefined és Null

### undefined
Ez az alapértelmezett érték, ha **nem adtunk kezdőértéket** a változónak.

```js
let x;
console.log(x); // undefined
```

### null
A `null` azt jelenti: **„tudatosan üres”**.  
Olyankor használjuk, amikor egy változónak **még nincs értéke, de később lesz**.

```js
let user = null;
user = "Anna";
console.log(user); // Anna
```

**Megjegyzés:** az `undefined` és `null` nem ugyanaz.  
`undefined` = nincs definiálva, `null` = szándékosan üres.

---

## Összetett típusok röviden

### Objektum (Object)
Kulcs–érték párokat tárol:
```js
const person = { name: "Anna", age: 25 };
console.log(person.name); // Anna
```

### Tömb (Array)
Rendezett lista, index alapján érhetők el az elemei:
```js
const fruits = ["alma", "banán", "körte"];
console.log(fruits[1]); // banán
```

### Függvény (Function)
Kódot tárol, amit többször is lefuttathatsz:
```js
function koszont(nev) {
  console.log(`Szia, ${nev}!`);
}

koszont("Béla");
```

---

## typeof – a típus lekérdezése

A `typeof` operátorral megnézheted, hogy egy változó milyen típusú.

```js
let szam = 42;
let szoveg = "Hello";
let logikai = true;

console.log(typeof szam);     // number
console.log(typeof szoveg);   // string
console.log(typeof logikai);  // boolean
```

**Furcsaság:**  
```js
console.log(typeof null); // "object"
```
Ez egy történelmi hiba a JavaScriptben, amit már nem változtattak meg a kompatibilitás miatt.

---

## Típuskonverzió (Type Conversion)

A JavaScript automatikusan is képes átalakítani típusokat, ha szükséges.  
Ezt hívják **implicit konverziónak**. Ha mi magunk alakítjuk át, az a **explicit konverzió**.

### Implicit (automatikus)

```js
let eredmeny = "5" + 3;  // "53" (összefűzés, nem összeadás)
let osszeg = "5" - 3;    // 2   (a - operátor számra alakítja)
```

A `+` operátor **összefűzést** végez, ha az egyik operandus string.  
Más műveletek (pl. `-`, `*`, `/`) viszont próbálják számra konvertálni az értékeket.

**Tipp:** mindig légy óvatos, ha számokat és szövegeket keversz!

### Explicit (kézzel megadott)

```js
let szoveg = "42";
let szam = Number(szoveg); // 42

let szam2 = 100;
let szoveg2 = String(szam2); // "100"

let logikai = Boolean(0); // false
```

### hasznos konverziós függvények:

| Függvény | Cél | Példa |
|-----------|------|--------|
| `Number()` | szöveget számmá | `Number("42") → 42` |
| `String()` | bármit szöveggé | `String(true) → "true"` |
| `Boolean()` | logikaivá | `Boolean("") → false` |
| `parseInt()` | egész számmá | `parseInt("3.14") → 3` |
| `parseFloat()` | tizedest is megőrzi | `parseFloat("3.14") → 3.14` |

---

## Truthy és Falsy értékek

A JavaScriptben minden érték **igaznak (truthy)** vagy **hamisnak (falsy)** számít, amikor logikai vizsgálat történik.

### Falsy értékek:
- `false`
- `0`
- `""` (üres string)
- `null`
- `undefined`
- `NaN`

Minden más érték **truthy**, tehát igaznak számít.

**Példa:**
```js
if ("Hello") {
  console.log("Ez igaz érték."); // Lefut
}

if (0) {
  console.log("Ez hamis érték."); // Nem fut le
}
```

---

## Tipikus hibák

⚠️ `"5" + 5` → `"55"` – mert a + stringet fűz össze.  
⚠️ `Number("Hello")` → `NaN` – nem alakítható számra.  
⚠️ `typeof null` → `"object"` – történelmi bug.  
⚠️ `Boolean("false")` → `true` – mert a nem üres string mindig igaz!

---

## Tippek

💡 Ha biztosra akarsz menni, **mindig kézzel konvertálj** típust (`Number()`, `String()`, `Boolean()`).  
💡 Használd a `typeof`-ot, ha nem vagy biztos, milyen adattal dolgozol.  
💡 Kerüld, hogy szöveget és számot keverj össze egy kifejezésben.  
💡 Az üres string (`""`) és a `0` logikailag hamisnak számítanak.  

---

## Összefoglalás

- A JavaScript dinamikus típusú nyelv — a típus futásidőben dől el.  
- Alaptípusok: `string`, `number`, `boolean`, `undefined`, `null`, `symbol`, `bigint`.  
- Összetett típusok: `object`, `array`, `function`.  
- `typeof` segítségével bármikor ellenőrizheted a típust.  
- A konverzió lehet automatikus vagy kézi, de mindig figyelj, mit vársz el.  

A következő fejezetben megnézzük, **hogyan végezhetünk műveleteket** ezekkel az adatokkal — azaz jönnek az **operátorok és kifejezések**!
