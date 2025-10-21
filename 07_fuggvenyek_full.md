# JavaScript függvények (function, return, paraméterek)

A programozásban a **függvények** segítenek abban, hogy ne kelljen ugyanazt a kódot többször megírni.  
Egy függvény tulajdonképpen **egy névvel ellátott kódrészlet**, amit bármikor újra felhasználhatsz.

Ha valaha azt érezted, hogy „ezt a logikát már megírtam máshol is”, akkor ideje volt függvényt csinálni belőle. 😊

---

## Mi az a függvény?

Egy függvény egy olyan kódblokk, ami **valamilyen feladatot elvégez**, majd **visszaadhat egy eredményt**.  
Lehet paraméterei (bemenő adatok) és visszatérési értéke (kimenet).

**Analógia:**  
A függvény olyan, mint egy kávéfőző:  
- bemenetként (paraméterként) kap kávét és vizet,  
- feldolgozza,  
- és kimenetként (return) kávét ad vissza. ☕

---

## Függvény létrehozása

A legegyszerűbb módja egy függvény létrehozásának a `function` kulcsszó használata.

```js
function koszont() {
  console.log("Szia, JavaScript!");
}
```

Itt a `koszont` a függvény neve, a kapcsos zárójelek között pedig az a kód, ami lefut, ha meghívjuk.

### Függvény meghívása

A függvény **nem fut le magától** – neked kell meghívni:

```js
koszont(); // Szia, JavaScript!
```

Minden alkalommal, amikor meghívod, lefut a benne lévő kód.

---

## Paraméterek és argumentumok

A paraméterek lehetővé teszik, hogy adatokat adj át a függvénynek.

```js
function udvozles(nev) {
  console.log("Szia, " + nev + "!");
}

udvozles("Anna");  // Szia, Anna!
udvozles("Béla");  // Szia, Béla!
```

- A **paraméter** (`nev`) a függvény definíciójában jelenik meg.  
- Az **argumentum** az a konkrét érték, amit meghíváskor adsz át (`"Anna"`).

### Több paraméter

```js
function osszeg(a, b) {
  console.log(a + b);
}

osszeg(5, 3); // 8
osszeg(10, 7); // 17
```

---

## return – visszatérési érték

A `return` kulcsszóval a függvény **visszaadhat egy eredményt**, amit később felhasználhatsz.

```js
function osszead(a, b) {
  return a + b;
}

let eredmeny = osszead(4, 6);
console.log(eredmeny); // 10
```

A `return` után a függvény **azonnal befejezi a futását**.  
Bármi, ami utána van, már nem hajtódik végre.

```js
function teszt() {
  return "Vége.";
  console.log("Ez már nem fut le.");
}
```

---

## Függvények egymásban

Függvények hívhatnak más függvényeket – ez a programozás alapja.

```js
function negyzet(x) {
  return x * x;
}

function osszegNegyzetek(a, b) {
  return negyzet(a) + negyzet(b);
}

console.log(osszegNegyzetek(3, 4)); // 25
```

---

## Függvényváltozók – anonim függvények

Egy függvényt akár változóban is tárolhatsz.

```js
const koszont = function() {
  console.log("Helló világ!");
};

koszont();
```

Ezt **névtelen függvénynek (anonymous function)** hívjuk, mert nincs saját neve – csak a változón keresztül hivatkozol rá.

---

## Arrow function (nyílfüggvény)

A **modern ES6** bevezetett egy rövidebb szintaxist: az **arrow function**-t (`=>`).

```js
const osszead = (a, b) => {
  return a + b;
};

console.log(osszead(2, 3)); // 5
```

Ha a függvény **csak egy utasítást** tartalmaz, és az visszatér egy értékkel, akkor még rövidebben is írható:

```js
const negyzet = x => x * x;

console.log(negyzet(5)); // 25
```

**Megjegyzés:** az arrow function **nem rendelkezik saját `this` értékkel**, ami fontos különbség objektumokon belül – erről később részletesebben lesz szó.

---

## Alapértelmezett paraméterek

Megadhatsz **alapértelmezett értéket** a paraméterekhez.  
Ha a függvényhíváskor nincs megadva argumentum, akkor az alapérték kerül felhasználásra.

```js
function koszont(nev = "ismeretlen") {
  console.log("Helló, " + nev + "!");
}

koszont();         // Helló, ismeretlen!
koszont("Anna");   // Helló, Anna!
```

---

## Paraméterek száma – arguments objektum

Ha nem tudod előre, hány argumentumot adnak át, a függvény belsejében elérhető az **`arguments` objektum**, ami minden átadott értéket tartalmaz.

```js
function osszead() {
  let osszeg = 0;
  for (let i = 0; i < arguments.length; i++) {
    osszeg += arguments[i];
  }
  return osszeg;
}

console.log(osszead(1, 2, 3)); // 6
console.log(osszead(10, 20, 30, 40)); // 100
```

Ez egy **beépített tömbszerű** objektum.

---

## Rest paraméter (modern megoldás)

A modern ES6-ban már a `...` operátorral könnyedén összegyűjtheted az összes argumentumot egy tömbbe.

```js
function osszeg(...szamok) {
  let total = 0;
  for (let n of szamok) {
    total += n;
  }
  return total;
}

console.log(osszeg(1, 2, 3, 4)); // 10
```

Ez a megoldás **olvasmányosabb** és ajánlottabb, mint az `arguments` használata.

---

## Függvények visszatérési érték nélkül

Nem minden függvény ad vissza értéket.  
Ilyenkor a visszatérési érték automatikusan `undefined` lesz.

```js
function logolas(uzenet) {
  console.log("LOG:", uzenet);
}

let eredmeny = logolas("Hello!");
console.log(eredmeny); // undefined
```

---

## Függvények, mint értékek

A JavaScriptben a függvény is **érték**, így paraméterként is átadható másik függvénynek.

```js
function udvozles() {
  console.log("Helló!");
}

function futtat(fv) {
  fv();
}

futtat(udvozles); // Helló!
```

Ezeket hívjuk **callback függvényeknek** – alapvető fontosságúak aszinkron kódban is (pl. időzítők, események, API-hívások).

---

## Függvény deklaráció vs. kifejezés

A két leggyakoribb függvénytípus:

1. **Deklaráció (Declaration):**  
   ```js
   function koszont() {
     console.log("Szia!");
   }
   ```

2. **Kifejezés (Expression):**  
   ```js
   const koszont = function() {
     console.log("Szia!");
   };
   ```

**Különbség:** a deklarált függvényeket **hoisting** miatt akár a definíciójuk előtt is meghívhatod, a kifejezéseket viszont nem.

```js
koszont(); // működik

function koszont() {
  console.log("Helló!");
}
```

De ez nem működne, ha `const koszont = function(){}` formát használnál.

---

## Tipikus hibák

⚠️ Elfelejtett `return` – a függvény mindig `undefined`-ot ad vissza.  
⚠️ Paraméter nevének elírása → `undefined` érték.  
⚠️ Túl sok vagy túl kevés argumentum → a hiányzók `undefined` lesznek.  
⚠️ Arrow function használata `this`-t igénylő kódban.  
⚠️ Függvény hívása `()` nélkül – ilyenkor csak hivatkozás történik, nem fut le.

---

## Tippek

💡 Mindig adj beszédes nevet a függvénynek – írja le, mit csinál.  
💡 Használj `return`-t, ha az eredményt később is fel akarod használni.  
💡 Az arrow function rövidebb, de kerüld, ha `this`-t használsz.  
💡 Alapértelmezett paramétereket adj meg, hogy elkerüld az `undefined`-ot.  
💡 A `rest` paraméter tökéletes változó hosszúságú argumentumlistákhoz.  

---

## Összefoglalás

- A függvény kódot kapszuláz, és újra felhasználhatóvá teszi.  
- Paraméterekkel adatokat adhatsz át neki.  
- A `return` segítségével visszaadhat egy értéket.  
- A modern `arrow function` rövidebb és elegánsabb.  
- A `rest` paraméter és az alapértékek megkönnyítik a munkát.  
- A függvények alapjai nélkülözhetetlenek minden JavaScript programban.  

A következő fejezetben megnézzük, **hogyan dolgozhatunk tömbökkel (arrays)** – a JavaScript egyik legfontosabb adatszerkezetével.
