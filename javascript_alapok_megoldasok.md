# JavaScript alapok – Gyakorlófeladatok mintamegoldások

A megoldások **Node.js** környezetben futtathatók. Minden feladathoz rövid magyarázatot is adok.

---

## 1) Üdvözlő program – változók, kiíratás

**Feladat:** Tárolj el egy nevet és egy életkort, majd írd ki: `Szia, Anna! 25 éves vagy.`

**Megoldás (`feladat01.js`):**
```js
const nev = "Anna";
const kor = 25;
console.log(`Szia, ${nev}! ${kor} éves vagy.`);
```
**Magyarázat:** Template literal-t (backtick) használunk a jól olvasható összefűzéshez.

---

## 2) Minimum, maximum, összeg – számok és logika

**Feladat:** Számold ki egy szám tömb **min**, **max** és **összeg** értékeit.

**Megoldás (`feladat02.js`):**
```js
const szamok = [3, 7, 2, 9, 4];

let min = szamok[0];
let max = szamok[0];
let osszeg = 0;

for (const n of szamok) {
  if (n < min) min = n;
  if (n > max) max = n;
  osszeg += n;
}

console.log(`min=${min}, max=${max}, osszeg=${osszeg}`);
```
**Magyarázat:** Végigmegyünk a tömbön; minden elemnél frissítjük a min/max értéket és halmozzuk az összeget.

---

## 3) FizzBuzz+ – elágazások és ciklus

**Feladat:** 1–30 között kiírás Fizz/Buzz/FizzBuzz szabállyal.

**Megoldás (`feladat03.js`):**
```js
for (let i = 1; i <= 30; i++) {
  if (i % 15 === 0) {
    console.log("FizzBuzz");
  } else if (i % 3 === 0) {
    console.log("Fizz");
  } else if (i % 5 === 0) {
    console.log("Buzz");
  } else {
    console.log(i);
  }
}
```
**Magyarázat:** A 3 és 5 egyszerre osztható számok a 15-tel oszthatók – ezt vizsgáljuk először.

---

## 4) Palindrom ellenőrző – string műveletek

**Feladat:** `isPalindrom(szoveg)` térjen vissza igaz/hamis értékkel.

**Megoldás (`feladat04.js`):**
```js
function isPalindrom(input) {
  const norm = input.toLowerCase().replace(/\s+/g, "");
  const rev = norm.split("").reverse().join("");
  return norm === rev;
}

// Próba
console.log(isPalindrom("geeg"));     // true
console.log(isPalindrom("A róka foka rA")); // true (szóköz és kis/nagy figyelmen kívül)
console.log(isPalindrom("alma"));     // false
```
**Magyarázat:** Normalizáljuk a szöveget (kisbetű, szóközök nélkül), majd összehasonlítjuk a megfordított változattal.

---

## 5) Tömb statisztika – átlag, párosak száma

**Feladat:** Számold átlagot (két tizedes) és páros elemek számát.

**Megoldás (`feladat05.js`):**
```js
const arr = [10, 15, 20, 21, 22];

let osszeg = 0;
let parosDb = 0;
for (const n of arr) {
  osszeg += n;
  if (n % 2 === 0) parosDb++;
}

const atlag = osszeg / arr.length;
console.log(`atlag=${atlag.toFixed(2)}, paros_db=${parosDb}`);
```
**Magyarázat:** `toFixed(2)`-vel formázzuk az átlagot; `n % 2 === 0` jelzi a páros számokat.

---

## 6) Gyakoriság-számláló – objektum, for...of

**Feladat:** Visszaadni az egyes karakterek előfordulási számát.

**Megoldás (`feladat06.js`):**
```js
function gyakorisag(szoveg) {
  const map = {};
  for (const ch of szoveg) {
    map[ch] = (map[ch] || 0) + 1;
  }
  return map;
}

// Próba
console.log(gyakorisag("abac")); // { a: 2, b: 1, c: 1 }
```
**Magyarázat:** Számláló objektum: ha a kulcs nincs beállítva, indul 0-ról.

---

## 7) Egyedi elemek – Set vagy manuális szűrés

**Feladat:** Adj vissza egyedi elemeket az eredeti sorrendben.

**Megoldás 1 – Set-tel (`feladat07a.js`):**
```js
function egyedi(arr) {
  return [...new Set(arr)];
}

console.log(egyedi([1,1,2,3,3,3,2,4])); // [1,2,3,4]
```

**Megoldás 2 – manuálisan (`feladat07b.js`):**
```js
function egyedi(arr) {
  const out = [];
  for (const x of arr) {
    if (!out.includes(x)) out.push(x);
  }
  return out;
}

console.log(egyedi([1,1,2,3,3,3,2,4])); // [1,2,3,4]
```
**Magyarázat:** A `Set` automatikusan kiszűri a duplikátumokat; manuálisan `includes`-szal ellenőrzünk.

---

## 8) Bevásárlókosár – összegzés, map/filter/reduce

**Feladat:** Nettó tételek szűrése és összege 27% ÁFÁ-val.

**Megoldás (`feladat08.js`):**
```js
const kosar = [
  { nev: "Alma", ar: 120, db: 2 },
  { nev: "Kenyer", ar: 600, db: 1 },
  { nev: "Korte", ar: 300, db: 0 }, // szűrendő
];

const nettoOsszeg = kosar
  .filter(t => t.db > 0 && t.ar > 0)
  .map(t => t.ar * t.db)
  .reduce((a, b) => a + b, 0);

const brutto = Math.round(nettoOsszeg * 1.27);
console.log(`vegosszeg_brutto=${brutto} Ft`);
```
**Magyarázat:** `filter` a hibás sorokra, `map` tételár számítás, `reduce` összegzés, végül 27% ÁFA és kerekítés.

---

## 9) Mini-kalkulátor függvény – paraméterezés

**Feladat:** `calc(a, b, muvelet)`; nullával osztás kezelése.

**Megoldás (`feladat09.js`):**
```js
function calc(a, b, muvelet) {
  switch (muvelet) {
    case "+": return a + b;
    case "-": return a - b;
    case "*": return a * b;
    case "/":
      if (b === 0) {
        console.error("Nem lehet nullával osztani!");
        return null;
      }
      return a / b;
    default:
      console.error("Ismeretlen művelet:", muvelet);
      return null;
  }
}

// Próba
console.log(calc(10, 5, "+")); // 15
console.log(calc(10, 0, "/")); // null (és hibaüzi)
```
**Magyarázat:** `switch` a tiszta elágazásért; hiba esetén `null`-lal tér vissza és logol.

---

## 10) Parancssori ToDo (mini projekt) – tömb + objektum + függvények

**Feladat:** Egyszerű ToDo-kezelő 4 művelettel.

**Megoldás (`feladat10.js`):**
```js
let kovId = 1;
const todos = [];

function hozzaad(cim) {
  const uj = { id: kovId++, cim, kesz: false };
  todos.push(uj);
  console.log(`Új teendő felvéve: "${cim}" (#${uj.id})`);
}

function listaz() {
  console.log("--- TODO ---");
  if (todos.length === 0) {
    console.log("(nincs teendő)");
    return;
  }
  for (const t of todos) {
    console.log(`${t.id}. [${t.kesz ? "x" : " "}] ${t.cim}`);
  }
}

function kesz(id) {
  const t = todos.find(x => x.id === id);
  if (!t) return console.error("Nincs ilyen ID:", id);
  t.kesz = true;
  console.log(`Készre állítva: #${id}`);
}

function torol(id) {
  const idx = todos.findIndex(x => x.id === id);
  if (idx === -1) return console.error("Nincs ilyen ID:", id);
  const [removed] = todos.splice(idx, 1);
  console.log(`Törölve: #${removed.id}`);
}

// Minta futtatás
hozzaad("Bevásárlás");
hozzaad("Edzés");
listaz();
kesz(1);
torol(2);
listaz();
```
**Magyarázat:** Állapot a `todos` tömbben; minden művelet külön függvény; `find`/`findIndex` segít a keresésben.
