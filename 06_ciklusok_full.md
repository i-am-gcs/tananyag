# JavaScript ciklusok (for, while, do...while)

A programozásban gyakran előfordul, hogy **ugyanazt a műveletet többször is végre kell hajtani**.  
Erre szolgálnak a **ciklusok** – vagy más néven ismétlő szerkezetek.

Ezek segítségével a program képes egy adott feltétel teljesüléséig újra és újra végrehajtani utasításokat, anélkül, hogy ugyanazt a kódot sokszor le kellene írni.

---

## Mi az a ciklus?

A ciklus (loop) olyan szerkezet, ami **addig ismétel egy kódrészt, amíg egy feltétel igaz**.

**Egyszerű példa:**

```js
for (let i = 1; i <= 5; i++) {
  console.log("Ez a", i, ". ismétlés.");
}
```

Ez a kód ötször fut le, és a kimenet a következő lesz:

```
Ez a 1 . ismétlés.
Ez a 2 . ismétlés.
Ez a 3 . ismétlés.
Ez a 4 . ismétlés.
Ez a 5 . ismétlés.
```

A ciklusok segítségével tehát **automatizáljuk az ismétlődő feladatokat**.

---

## Miért hasznosak a ciklusok?

Képzeld el, hogy 100 számot szeretnél kiírni a konzolra.  
Kézzel leírni 100 `console.log()` sort szinte lehetetlen – de egy ciklus néhány sorban megoldja.

```js
for (let i = 1; i <= 100; i++) {
  console.log(i);
}
```

A program mindössze **három sorral** elvégzi ugyanazt a munkát.

---

## A ciklusok fajtái

A JavaScriptben három alap ciklus létezik:

1. `for` – ha előre tudjuk, **hányszor** kell ismételni  
2. `while` – ha csak a **feltétel** ismert, nem a lépésszám  
3. `do...while` – ha legalább **egyszer** mindenképp le kell futnia

---

## 1. for ciklus

A `for` ciklus három részből áll:  
1️⃣ **Inicializálás** (pl. `let i = 0;`) – egyszer fut le a ciklus elején.  
2️⃣ **Feltétel** (pl. `i < 10;`) – minden körben ellenőrzi.  
3️⃣ **Léptetés** (pl. `i++`) – minden kör végén végrehajtódik.

**Szintaxis:**
```js
for (inicializálás; feltétel; léptetés) {
  // a kód, ami ismétlődik
}
```

**Példa:**
```js
for (let i = 0; i < 5; i++) {
  console.log("A számláló értéke:", i);
}
```

Kimenet:
```
A számláló értéke: 0
A számláló értéke: 1
A számláló értéke: 2
A számláló értéke: 3
A számláló értéke: 4
```

---

### Fordított irányú ciklus

```js
for (let i = 10; i >= 1; i--) {
  console.log(i);
}
```

Ez a kód **visszafelé számol 10-től 1-ig**.

---

### Többszörös léptetés

```js
for (let i = 0; i <= 20; i += 5) {
  console.log(i);
}
```

Kimenet: `0 5 10 15 20`

A `i += 5` azt jelenti, hogy minden körben **5-tel növeljük** az értéket.

---

## 2. while ciklus

A `while` ciklus addig ismétel, **amíg a feltétel igaz**.

**Szintaxis:**
```js
while (feltétel) {
  // a kód, ami ismétlődik
}
```

**Példa:**
```js
let i = 0;

while (i < 5) {
  console.log("A számláló:", i);
  i++;
}
```

Ez ugyanazt csinálja, mint az előző `for` ciklus.

---

### Végtelen ciklus – vigyázz! ⚠️

Ha a feltétel **sosem lesz hamis**, a ciklus végtelenül fut – és a program nem áll le.

```js
let i = 0;

while (true) {
  console.log(i);
  i++;
}
```

**Mindig gondoskodj róla, hogy a feltétel előbb-utóbb hamisra váltson!**

---

## 3. do...while ciklus

A `do...while` ciklus **legalább egyszer** lefut, még akkor is, ha a feltétel hamis.

**Szintaxis:**
```js
do {
  // a kód, ami ismétlődik
} while (feltétel);
```

**Példa:**
```js
let j = 10;

do {
  console.log("Legalább egyszer lefut.");
  j++;
} while (j < 5);
```

A kód egyszer lefut, mert a feltételt **csak utólag** ellenőrzi.

---

## break és continue

Két speciális kulcsszóval irányíthatod a ciklusok működését.

### break – kilépés a ciklusból

A `break` azonnal megszakítja a ciklust.

```js
for (let i = 1; i <= 10; i++) {
  if (i === 5) break;
  console.log(i);
}
```

Kimenet: `1 2 3 4`  
Amint `i` eléri az 5-öt, a ciklus leáll.

---

### continue – kihagy egy iterációt

A `continue` azt jelenti: **ugorjuk át a jelenlegi kört**, és menjünk tovább a következőre.

```js
for (let i = 1; i <= 5; i++) {
  if (i === 3) continue;
  console.log(i);
}
```

Kimenet: `1 2 4 5`  
A 3-as kimarad, de a ciklus nem áll meg.

---

## beágyazott ciklusok

Ciklusok egymásba is ágyazhatók, ha például táblázatokat, mátrixokat vagy többszintű adatszerkezeteket dolgozol fel.

```js
for (let i = 1; i <= 3; i++) {
  for (let j = 1; j <= 2; j++) {
    console.log(`Külső: ${i}, Belső: ${j}`);
  }
}
```

Kimenet:
```
Külső: 1, Belső: 1
Külső: 1, Belső: 2
Külső: 2, Belső: 1
Külső: 2, Belső: 2
Külső: 3, Belső: 1
Külső: 3, Belső: 2
```

---

## Végtelen ciklusok és kilépési feltételek

Néha szándékosan végtelen ciklust írunk, de **feltételes kilépéssel** kombinálva.

**Példa:**
```js
let i = 0;

while (true) {
  console.log(i);
  if (i === 4) break;
  i++;
}
```

Ez csak 0–4-ig fut, mert a `break` megszakítja.

---

## For...of és For...in ciklusok

A JavaScriptben két modern, gyakran használt ciklus is van.

### for...of – tömbök bejárásához
```js
const gyumolcsok = ["alma", "banán", "körte"];

for (let gyumolcs of gyumolcsok) {
  console.log(gyumolcs);
}
```

Kimenet:
```
alma
banán
körte
```

### for...in – objektum tulajdonságok bejárásához
```js
const szemely = { nev: "Anna", kor: 25, varos: "Budapest" };

for (let kulcs in szemely) {
  console.log(kulcs + ": " + szemely[kulcs]);
}
```

Kimenet:
```
nev: Anna
kor: 25
varos: Budapest
```

---

## Tipikus hibák

⚠️ Elfelejtett léptetés → végtelen ciklus  
⚠️ Feltétel hibás → a ciklus sosem fut le  
⚠️ `=` (értékadás) helyett `==` vagy `===` kellett volna  
⚠️ Beágyazott ciklusban elfelejtett változó újrainicializálása  
⚠️ `for...in` tömbökhöz → nem ajánlott (használd inkább `for...of`)  

---

## Tippek

💡 Ha tudod, hányszor kell ismételni → használj `for` ciklust.  
💡 Ha csak a feltétel számít → `while`.  
💡 Ha legalább egyszer mindenképp futnia kell → `do...while`.  
💡 Mindig gondoskodj a ciklus megszakításáról (`break`).  
💡 Használd a `for...of` és `for...in` formákat modern, tiszta kódhoz.  

---

## Összefoglalás

- A ciklusok ismétlődő feladatokat automatizálnak.  
- `for` – ha ismert az ismétlések száma.  
- `while` – ha csak a feltétel ismert.  
- `do...while` – ha legalább egyszer futnia kell.  
- `break` és `continue` segít irányítani a ciklus futását.  
- `for...of` és `for...in` kényelmes eszközök tömbökhöz és objektumokhoz.  

A következő fejezetben megnézzük a **függvényeket**, vagyis hogyan tudsz saját, újrahasználható logikai egységeket létrehozni a programban.
