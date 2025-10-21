# JavaScript változók és konstansok (var, let, const)

A JavaScriptben minden adatot valahol el kell tárolni, hogy a program később is hozzáférjen.  
Ezt a célt szolgálják a **változók** és a **konstansok**.  
A változó olyan, mint egy névvel ellátott tároló, amiben adatot őrzünk.  
A konstans pedig ugyanilyen tároló, csak az értékét **nem lehet megváltoztatni**.

---

## Mik azok a változók?

A változók az adatok tárolására szolgálnak.  
Egy változóban bármilyen típusú értéket elmenthetsz: számot, szöveget, logikai értéket vagy akár objektumot is.  

**Egyszerű példa:**

```js
let uzenet = "Szia, JavaScript!";
console.log(uzenet); // Szia, JavaScript!
```

A fenti kódban létrehoztunk egy `uzenet` nevű változót, és egy szöveget tároltunk benne.  
Ezután a `console.log()` segítségével kiírtuk az értékét a konzolra.

**Analógia:**  
A változó olyan, mint egy doboz, amire ráírsz egy nevet (pl. „cukor”), és beleteszel valamit.  
Ha később kicseréled a doboz tartalmát, a neve ugyanaz marad, de a belseje megváltozik.

---

## A var, let és const története

A JavaScript korai verzióiban (ES5 előtt) csak a **`var`** kulcsszó létezett változók létrehozására.  
Ez azonban sok hibát okozott, mert a `var` nem korlátozta megfelelően a változó élettartamát és láthatóságát.  

2015-ben (az **ES6** verzióban) bevezették a **`let`** és **`const`** kulcsszavakat,  
amik sokkal kiszámíthatóbb és biztonságosabb működést adnak.

| Kulcsszó | Lehet újra értéket adni? | Lehet újra létrehozni ugyanazzal a névvel? | Láthatóság |
|-----------|----------------------------|---------------------------------------------|-------------|
| var | ✅ igen | ✅ igen | függvény (function) szintű |
| let | ✅ igen | ❌ nem | blokk szintű |
| const | ❌ nem | ❌ nem | blokk szintű |

---

## A var használata (régi módszer)

```js
var nev = "Anna";
console.log(nev); // Anna

var nev = "Béla"; // újra létrehozható
console.log(nev); // Béla
```

A `var` változókat akár többször is létrehozhatod ugyanazzal a névvel, ami zavaros hibákhoz vezethet.  
Ezen kívül a `var` úgynevezett **hoisting** hatás alatt áll: a JavaScript „felhúzza” a változó deklarációját a kód elejére.

**Ezért manapság már nem ajánlott a használata.**

---

## A let használata (modern, ajánlott)

A `let` a leggyakrabban használt módja a változók létrehozásának.  
Az értéke megváltoztatható, de a névvel nem hozható létre újra.

```js
let kor = 18;
console.log(kor); // 18

kor = 19; // az érték módosítható
console.log(kor); // 19

// let kor = 20; // ❌ Hiba, már létezik ilyen nevű változó
```

A `let` csak azon a **blokkon belül** érvényes, ahol létrehoztad.  
Például egy `if` vagy `for` ciklusban létrehozott `let` változó nem látható azon kívül.

```js
if (true) {
  let uzenet = "Csak itt elérhető";
  console.log(uzenet); // működik
}
// console.log(uzenet); // ❌ Hiba – itt már nem létezik
```

---

## A const használata (állandó értékekhez)

A `const` segítségével **állandó értékeket** tudsz létrehozni, amiket nem lehet felülírni.  
Ezt használjuk, ha valami nem fog változni a program futása során.

```js
const PI = 3.14159;
console.log(PI);

// PI = 3; // ❌ Hiba, a const értéke nem módosítható
```

A `const`-tal létrehozott változók kötelezően kapjanak **kezdőértéket**, különben hibát okoznak:

```js
// const szam; // ❌ Hiba: nincs kezdőérték
const szam = 42; // ✅ helyes
```

**Tipp:** ha valamit véletlenül sem akarsz átírni, használd a `const`-ot.

---

## Változók elnevezése – a jó szokások

A JavaScriptben a változók neve szinte bármi lehet, de néhány szabályt be kell tartani:

✅ A név:
- csak **betűvel**, **aláhúzással (_)** vagy **dollárjellel ($)** kezdődhet,
- tartalmazhat **számokat**, de nem kezdődhet számmal,
- **kis- és nagybetű érzékeny** (`nev` és `Nev` két külön dolog),
- **nem lehet JavaScript kulcsszó** (pl. `let`, `if`, `for`, `class`, stb.).

### Példák

```js
let nev = "Anna";     // helyes
let _kor = 25;        // helyes
let $fizetes = 3000;  // helyes
let 1nev = "Béla";    // ❌ hibás
let let = "valami";   // ❌ hibás
```

**Tipp:** Használj beszédes, önmagáért beszélő neveket:  
`felhasznaloNev`, `eletkor`, `osszeg`, `rendelesLista`.

---

## Változó létrehozása értékkel

A leggyakoribb forma: **deklarálás és értékadás egyben**.

```js
let nev = "Anna";
let kor = 25;
let diak = true;
```

A JavaScript automatikusan felismeri, milyen típusú adatot tárolsz:  
- `"Anna"` → string (szöveg)  
- `25` → number (szám)  
- `true` → boolean (logikai érték)

---

## Változó létrehozása érték nélkül

Néha csak előkészíted a változót, és majd később adsz neki értéket:

```js
let ertek;
console.log(ertek); // undefined

ertek = 42;
console.log(ertek); // 42
```

Ha egy változónak még nincs értéke, automatikusan `undefined` lesz.

---

## Több változó egyszerre

Egyszerre több változót is létrehozhatsz, vesszővel elválasztva:

```js
let nev = "Anna", kor = 25, varos = "Budapest";
```

Ez működik `var` és `const` esetén is, de olvashatóság szempontjából **jobb külön sorba írni őket.**

---

## Érték módosítása

Ha egy változó **nem konstans**, bármikor megváltoztathatod az értékét.

```js
let kor = 18;
kor = 19;
kor = 20;

console.log(kor); // 20
```

A `const` esetében ez hibát okozna.

---

## Műveletek változókkal

A változók értékeivel mindenféle műveletet végezhetsz.

### Matematikai műveletek

```js
let a = 5;
let b = 10;

console.log(a + b); // 15
console.log(a * b); // 50
console.log(b - a); // 5
console.log(b / a); // 2
```

### Szövegek összefűzése

```js
let firstName = "Anna";
let lastName = "Kovács";
let fullName = firstName + " " + lastName;

console.log(fullName); // Anna Kovács
```

### Template literal (modern forma)

```js
let name = "Béla";
let age = 30;

console.log(`Szia, ${name}! ${age} éves vagy.`);
```

Ez olvashatóbb, mint a sima összefűzés.

---

## Típusok röviden

| Típus | Példa | Jelentés |
|-------|--------|-----------|
| string | `"Hello"` | szöveg |
| number | `42` | szám |
| boolean | `true` | logikai érték |
| undefined | – | nincs érték |
| object | `{ nev: "Anna", kor: 25 }` | összetett adat |
| array | `["alma", "banán"]` | lista |

---

## Tippek

💡 **`let` legyen az alapértelmezett.**  
Ha biztos vagy benne, hogy nem változik, használd a `const`-ot.  

💡 Adj beszédes neveket a változóknak – ne `x`, hanem `osszPont` vagy `felhasznaloNev`.  

💡 A `var` régi, kerüld el, mert zavaró hibákat okozhat.  

💡 A `console.log()` a legjobb barátod hibakereséskor – bármikor meg tudod nézni, mi van a változóban.

---

## Összefoglalás

- A változók adatokat tárolnak.  
- A `let` módosítható, a `const` fix, a `var` elavult.  
- A változókat értékkel vagy anélkül is létrehozhatod.  
- Érdemes mindig beszédes neveket használni.  
- A JavaScript automatikusan felismeri az adattípust.  

A következő részben megnézzük, **milyen adattípusokat ismer a JavaScript**,  
és hogyan viselkednek a különböző típusú értékek a műveletek során.
