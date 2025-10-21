# JavaScript objektumok (Objects)

A JavaScriptben **minden objektum** – az adatok, a függvények, sőt még a tömbök is.  
Az objektum az egyik **legfontosabb adatszerkezet**, mert segítségével **összetett információkat** tudunk egy helyen tárolni.

Gondolj egy objektumra úgy, mint egy **dokumentumra tele címkézett adatokkal**: név, kor, város – mindegyikhez tartozik egy érték.

---

## Mi az az objektum?

Egy objektum **kulcs–érték párokat** (key–value pairs) tartalmaz.  
A kulcs mindig **string típus**, az érték pedig **bármi lehet** – szám, string, függvény, vagy akár másik objektum is.

**Példa:**

```js
let ember = {
  nev: "Anna",
  kor: 25,
  varos: "Budapest"
};
```

Itt:
- `nev`, `kor`, `varos` → **kulcsok** (key)  
- `"Anna"`, `25`, `"Budapest"` → **értékek** (value)

---

## Objektum létrehozása

### 1️⃣ Objektumliterál (ajánlott forma)

```js
let auto = {
  marka: "Toyota",
  evjarat: 2020,
  szin: "piros"
};
```

### 2️⃣ new Object() konstruktorral

```js
let auto = new Object();
auto.marka = "Toyota";
auto.evjarat = 2020;
auto.szin = "piros";
```

A modern JavaScriptben **mindig az objektumliterálos formát** használd (`{}`), mert egyszerűbb és olvashatóbb.

---

## Objektum tulajdonságainak elérése

Kétféle módon érheted el egy objektum értékeit:

### 1️⃣ Pont (dot) notáció
```js
console.log(ember.nev); // Anna
```

### 2️⃣ Zárójel (bracket) notáció
```js
console.log(ember["kor"]); // 25
```

A zárójeles forma akkor kell, ha:
- a kulcs **változóban** van tárolva, vagy
- a kulcs **különleges karaktert / szóközt** tartalmaz.

```js
let kulcs = "varos";
console.log(ember[kulcs]); // Budapest
```

---

## Új tulajdonság hozzáadása

```js
ember.foglalkozas = "fejlesztő";
console.log(ember);
```

Eredmény:
```js
{ nev: "Anna", kor: 25, varos: "Budapest", foglalkozas: "fejlesztő" }
```

---

## Tulajdonság módosítása és törlése

### Módosítás:
```js
ember.kor = 26;
```

### Törlés:
```js
delete ember.varos;
```

---

## Objektum metódusok – függvények objektumban

Ha egy objektumon belül függvényt tárolunk, azt **metódusnak** nevezzük.

```js
let ember = {
  nev: "Anna",
  koszont: function() {
    console.log("Szia, " + this.nev + "!");
  }
};

ember.koszont(); // Szia, Anna!
```

A `this` kulcsszó mindig **arra az objektumra hivatkozik**, amelyben éppen vagyunk.

---

## Rövidített metódus szintaxis (modern ES6)

```js
let ember = {
  nev: "Béla",
  koszont() {
    console.log(`Helló, ${this.nev}!`);
  }
};

ember.koszont(); // Helló, Béla!
```

Ez rövidebb és tisztább forma, mint a régi `koszont: function()` változat.

---

## this kulcsszó

A `this` dinamikusan változik attól függően, **milyen környezetben** hívjuk a függvényt.

```js
let szemely = {
  nev: "Anna",
  koszont() {
    console.log("Szia, " + this.nev);
  }
};

szemely.koszont(); // Szia, Anna
```

De ha az objektum metódusát egy másik változóba másolod, elveszik a `this`-hez tartozó kontextus:

```js
let fn = szemely.koszont;
fn(); // Szia, undefined
```

Az arrow function-ök **nem rendelkeznek saját `this`-sel**, így gyakran más viselkedést mutatnak.

---

## Objektum bejárása (iterálás)

### for...in ciklus

```js
let auto = { marka: "Ford", evjarat: 2018, szin: "kék" };

for (let kulcs in auto) {
  console.log(kulcs + ": " + auto[kulcs]);
}
```

Kimenet:
```
marka: Ford
evjarat: 2018
szin: kék
```

---

## Objektum kulcsainak és értékeinek kezelése

A JavaScript beépített metódusokat ad az objektumok bejárásához:

| Metódus | Mit ad vissza |
|----------|----------------|
| `Object.keys(obj)` | kulcsokat tartalmazó tömb |
| `Object.values(obj)` | értékeket tartalmazó tömb |
| `Object.entries(obj)` | [kulcs, érték] párok tömbjét |

**Példa:**
```js
let auto = { marka: "BMW", evjarat: 2021 };

console.log(Object.keys(auto));   // ["marka", "evjarat"]
console.log(Object.values(auto)); // ["BMW", 2021]
console.log(Object.entries(auto)); // [["marka", "BMW"], ["evjarat", 2021]]
```

---

## Objektum másolása

A JavaScriptben az objektumok **referenciaként** tárolódnak – vagyis ha másolod őket, valójában **ugyanarra a memóriacímre** mutatnak.

```js
let eredeti = { nev: "Anna" };
let masolat = eredeti;

masolat.nev = "Béla";

console.log(eredeti.nev); // Béla ❌
```

### Helyes másolás (shallow copy)

Használd a **spread operátort (`...`)** vagy az `Object.assign()` metódust.

```js
let eredeti = { nev: "Anna", kor: 25 };

// Spread operátor
let masolat1 = { ...eredeti };

// Object.assign()
let masolat2 = Object.assign({}, eredeti);
```

Mindkettő új objektumot hoz létre, nem csak hivatkozást.

---

## Objektumok összefűzése

Két objektumot könnyedén összevonhatsz:

```js
let ember = { nev: "Anna" };
let adatok = { kor: 25, varos: "Budapest" };

let egyesitett = { ...ember, ...adatok };
console.log(egyesitett);
// { nev: "Anna", kor: 25, varos: "Budapest" }
```

---

## Beágyazott objektumok

Objektumokon belül más objektumokat is tárolhatsz.

```js
let szemely = {
  nev: "Anna",
  cim: {
    varos: "Budapest",
    iranyitoszam: 1111
  }
};

console.log(szemely.cim.varos); // Budapest
```

---

## Objektum destrukturálás

A destructuring segítségével egyszerűen kibonthatod az objektum adatait változókba.

```js
let ember = { nev: "Anna", kor: 25, varos: "Győr" };

let { nev, kor } = ember;
console.log(nev); // Anna
console.log(kor); // 25
```

---

## Rövidített tulajdonságnevek

Ha a változó neve megegyezik a kulcs nevével, elég egyszer megadni.

```js
let nev = "Anna";
let kor = 25;

let ember = { nev, kor };
console.log(ember); // { nev: "Anna", kor: 25 }
```

---

## Objektumok tömbökben

Nagyon gyakori, hogy több objektumot **egy tömbben** tárolunk.

```js
let emberek = [
  { nev: "Anna", kor: 25 },
  { nev: "Béla", kor: 30 },
  { nev: "Csaba", kor: 28 }
];

for (let ember of emberek) {
  console.log(`${ember.nev} ${ember.kor} éves.`);
}
```

---

## Objektum metódusai (hasOwnProperty, freeze, seal)

| Metódus | Leírás |
|----------|--------|
| `obj.hasOwnProperty("kulcs")` | Ellenőrzi, hogy az adott kulcs közvetlenül az objektumban van-e |
| `Object.freeze(obj)` | „befagyasztja” az objektumot – nem módosítható |
| `Object.seal(obj)` | nem lehet új kulcsokat hozzáadni vagy törölni |

**Példa:**
```js
let szemely = { nev: "Anna" };
Object.freeze(szemely);

szemely.nev = "Béla"; // nem történik semmi
console.log(szemely.nev); // Anna
```

---

## Tipikus hibák

⚠️ A `this` értéke függ attól, **hogyan** hívod meg a függvényt.  
⚠️ Az objektumok másolása referencia szerint történik, hacsak nem használsz spread-et vagy assign-t.  
⚠️ A `for...in` nem garantál sorrendet.  
⚠️ Ha egy kulcsot nem találsz, az eredmény `undefined` lesz.  
⚠️ Az `Object.freeze()` után nem lehet módosítani semmit.  

---

## Tippek

💡 Használj objektumliterált (`{}`), ne `new Object()`-ot.  
💡 A spread (`...`) a legegyszerűbb mód másolásra és összefűzésre.  
💡 A destrukturálás olvashatóbbá teszi a kódot.  
💡 Az objektumok tömbökben való tárolása remek adatmodell-listákhoz.  
💡 Mindig figyelj a `this` kontextusra – különösen arrow function-ök esetén.  

---

## Összefoglalás

- Az objektum kulcs–érték párokat tartalmazó adatszerkezet.  
- Pont (`.`) és zárójel (`[]`) notációval férhetsz hozzá.  
- A metódusok az objektumon belüli függvények.  
- A `this` mindig az aktuális objektumot jelenti.  
- A spread (`...`) és destrukturálás modern, tiszta megoldások.  
- Az objektumok a JavaScript alapjai – minden fejlettebb szerkezet rájuk épül.  

A következő fejezetben megnézzük, **hogyan dolgozhatunk eseményekkel és interaktív kóddal a böngészőben** – jön a **DOM és eseménykezelés**!
