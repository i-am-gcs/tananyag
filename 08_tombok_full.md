# JavaScript tömbök (Arrays)

A **tömb** (angolul *array*) az egyik legfontosabb adatszerkezet a JavaScriptben.  
Arra használjuk, hogy **több adatot egyetlen változóban** tároljunk.  
Olyan, mintha egy fiók lenne, amiben sok kis rekesz van — mindegyikben egy-egy érték.

---

## Mi az a tömb?

A tömb egy **rendezett lista**, amelyben az elemeket **indexek** segítségével érhetjük el.  
A tömb indexelése mindig **0-tól kezdődik** – tehát az első elem indexe `0`, a másodiké `1`, és így tovább.

**Példa:**

```js
let gyumolcsok = ["alma", "banán", "körte"];
```

- `gyumolcsok[0]` → `"alma"`  
- `gyumolcsok[1]` → `"banán"`  
- `gyumolcsok[2]` → `"körte"`

```js
console.log(gyumolcsok[0]); // alma
```

---

## Tömb létrehozása

Tömböt kétféleképpen hozhatsz létre:

### 1️⃣ Szögletes zárójelekkel (ajánlott)
```js
let szamok = [1, 2, 3, 4, 5];
```

### 2️⃣ Array konstruktorral
```js
let szamok = new Array(1, 2, 3, 4, 5);
```

A modern JavaScriptben **mindig a szögletes zárójeles formát** használd – rövidebb és olvashatóbb.

---

## Tömb elemeinek elérése és módosítása

A tömb elemeihez az index segítségével férsz hozzá:

```js
let nevek = ["Anna", "Béla", "Csaba"];
console.log(nevek[1]); // Béla
```

### Elem módosítása:
```js
nevek[1] = "Balázs";
console.log(nevek); // ["Anna", "Balázs", "Csaba"]
```

---

## Tömb hossza

A `length` tulajdonság megadja, hány elem van a tömbben.

```js
let szamok = [10, 20, 30, 40];
console.log(szamok.length); // 4
```

**Tipp:** a `length` segítségével könnyen végigjárhatod a tömböt:

```js
for (let i = 0; i < szamok.length; i++) {
  console.log(szamok[i]);
}
```

---

## Elemszám dinamikus bővítése

Ha a tömb végére új elemet szeretnél hozzáadni:

```js
let szamok = [1, 2, 3];
szamok.push(4);
console.log(szamok); // [1, 2, 3, 4]
```

### Másik mód: indexeléssel
```js
szamok[szamok.length] = 5;
console.log(szamok); // [1, 2, 3, 4, 5]
```

---

## Fontos tömbmetódusok

A JavaScript rengeteg beépített metódust ad a tömbök kezelésére.  
Nézzük a leggyakoribbakat!

| Metódus | Mit csinál | Példa |
|----------|-------------|--------|
| `push()` | Hozzáad egy elemet a végére | `arr.push("elem")` |
| `pop()` | Eltávolítja az utolsó elemet | `arr.pop()` |
| `unshift()` | Hozzáad elemet az elejére | `arr.unshift("elem")` |
| `shift()` | Eltávolítja az első elemet | `arr.shift()` |
| `indexOf()` | Megadja egy elem indexét | `arr.indexOf("alma")` |
| `includes()` | Megmondja, tartalmazza-e az elemet | `arr.includes("alma")` |
| `slice()` | Kivág egy részt (nem módosítja az eredetit) | `arr.slice(1,3)` |
| `splice()` | Töröl vagy behelyettesít elemeket | `arr.splice(1, 2)` |
| `concat()` | Összefűz két tömböt | `arr1.concat(arr2)` |
| `join()` | Szöveggé alakítja | `arr.join(", ")` |

---

## Példa – tömbök manipulálása

```js
let gyumolcsok = ["alma", "banán", "körte"];
gyumolcsok.push("szilva");
console.log(gyumolcsok); // ["alma", "banán", "körte", "szilva"]

gyumolcsok.pop();
console.log(gyumolcsok); // ["alma", "banán", "körte"]

gyumolcsok.unshift("narancs");
console.log(gyumolcsok); // ["narancs", "alma", "banán", "körte"]

gyumolcsok.splice(1, 1, "citrom");
console.log(gyumolcsok); // ["narancs", "citrom", "banán", "körte"]
```

---

## Tömb bejárása (iterálás)

A tömb elemein **többféle módon** is végigmehetsz:

### 1️⃣ for ciklus
```js
let szamok = [1, 2, 3, 4];
for (let i = 0; i < szamok.length; i++) {
  console.log(szamok[i]);
}
```

### 2️⃣ for...of ciklus
```js
for (let szam of szamok) {
  console.log(szam);
}
```

### 3️⃣ forEach metódus
```js
szamok.forEach(function(szam) {
  console.log(szam);
});
```

Modern formában:
```js
szamok.forEach(szam => console.log(szam));
```

---

## Tömbök átalakítása – map, filter, reduce

Ezek a metódusok az adatok feldolgozásában segítenek.

### map() – minden elemre műveletet végez
```js
let szamok = [1, 2, 3];
let duplazott = szamok.map(x => x * 2);
console.log(duplazott); // [2, 4, 6]
```

### filter() – kiszűri az elemeket feltétel alapján
```js
let szamok = [1, 2, 3, 4, 5];
let parosak = szamok.filter(x => x % 2 === 0);
console.log(parosak); // [2, 4]
```

### reduce() – egy értékké alakítja az egész tömböt
```js
let szamok = [1, 2, 3, 4];
let osszeg = szamok.reduce((a, b) => a + b, 0);
console.log(osszeg); // 10
```

---

## Tömb rendezése – sort()

A `sort()` metódus rendezi a tömb elemeit **alfabetikusan** (alapértelmezésben).

```js
let nevek = ["Béla", "Anna", "Csaba"];
nevek.sort();
console.log(nevek); // ["Anna", "Béla", "Csaba"]
```

Számoknál viszont óvatosan, mert a `sort()` szövegként hasonlít össze!

```js
let szamok = [1, 5, 10, 2];
szamok.sort();
console.log(szamok); // [1, 10, 2, 5] ❌
```

Használj **összehasonlító függvényt**:

```js
szamok.sort((a, b) => a - b);
console.log(szamok); // [1, 2, 5, 10] ✅
```

---

## Tömbök másolása és összefűzése

### Másolás – spread operátorral (`...`)
```js
let eredeti = [1, 2, 3];
let masolat = [...eredeti];

masolat.push(4);
console.log(eredeti); // [1, 2, 3]
console.log(masolat); // [1, 2, 3, 4]
```

### Összefűzés – több tömbből egyet
```js
let a = [1, 2];
let b = [3, 4];
let ossze = [...a, ...b];
console.log(ossze); // [1, 2, 3, 4]
```

---

## Tömbök destrukturálása

A **destructuring** lehetővé teszi, hogy egyszerűen „szétszedd” a tömböt változókra.

```js
let szinek = ["piros", "zöld", "kék"];
let [elso, masodik] = szinek;

console.log(elso); // piros
console.log(masodik); // zöld
```

---

## Tömbök speciális típusai

### Kétdimenziós tömbök (tömbök tömbje)
```js
let matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];

console.log(matrix[1][2]); // 6
```

Ilyeneket használunk például **táblázatok**, **játéktáblák**, vagy **koordináták** esetén.

---

## Tipikus hibák

⚠️ Indexelés 0-tól indul – az utolsó elem indexe mindig `length - 1`.  
⚠️ `sort()` számokkal szövegként viselkedik, ha nincs összehasonlító függvény.  
⚠️ `splice()` **módosítja** az eredeti tömböt, a `slice()` nem.  
⚠️ Üres tömb `[]` truthy érték (nem hamis a feltételekben).  
⚠️ A `for...in` ciklust ne használd tömbökhöz (objektumhoz való).  

---

## Tippek

💡 Használd a `for...of` vagy `forEach()` metódust a tiszta bejáráshoz.  
💡 A `map()`, `filter()` és `reduce()` funkcionális stílusban segítenek adatok feldolgozásában.  
💡 Használd a spread (`...`) operátort tömbök másolásához vagy összefűzéséhez.  
💡 Ne feledd: a `sort()` mindig szövegként rendez, hacsak nem írsz összehasonlítót.  
💡 A `const` tömb elemei módosíthatók – csak maga a referencia nem változhat.  

---

## Összefoglalás

- A tömb több értéket tárol egyetlen változóban.  
- Az elemeket index alapján érjük el (0-tól indul).  
- Sok beépített metódus segíti a módosítást és átalakítást.  
- A `map()`, `filter()`, `reduce()` a leggyakrabban használt funkciók közé tartozik.  
- A spread és destrukturálás modern, tiszta megoldásokat kínál.  

A következő fejezetben megnézzük, **hogyan dolgozhatunk objektumokkal (objects)** – az adatok összetettebb tárolási formájával.
