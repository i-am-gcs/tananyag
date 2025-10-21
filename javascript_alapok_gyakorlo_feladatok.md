# JavaScript alapok – 10 gyakorlófeladat (VS Code + Node.js)

Ezek a feladatok **konzolos** (Node.js) környezetben futtathatók.  
Mindegyik feladat célja, hogy gyakorold az **alap JS fogalmakat**: változók, típusok, elágazások, ciklusok, függvények, tömbök, objektumok, hibakeresés.

> Tipp: Hozz létre egy mappát (pl. `gyakorlo/`), és minden feladathoz egy külön fájlt (pl. `feladat01.js`).  
> Futtatás: `node feladat01.js`

---

## 1) Üdvözlő program – változók, kiíratás

**Cél:** változók, string-összefűzés és template literal gyakorlása.

**Feladat:** Tárolj el egy nevet és egy életkort változókban, majd írd ki így:  
`Szia, Anna! 25 éves vagy.`

**Példa kimenet:**
```
Szia, Anna! 25 éves vagy.
```

**Tipp:** használj template literalt: `` `Szia, ${nev}! ${kor} éves vagy.` ``

**Starter:**
```js
const nev = "Anna";
const kor = 25;

// Ide jön a kiíratás
```

---

## 2) Minimum, maximum, összeg – számok és logika

**Cél:** alap műveletek, összehasonlítás, tömb bejárása.

**Feladat:** Adott egy tömb számokkal. Számold ki a **minimumot**, **maximumot** és az **összeget**, majd írd ki egy sorban.

**Bemenet (a kódban):**
```js
const szamok = [3, 7, 2, 9, 4];
```

**Elvárt kimenet:**
```
min=2, max=9, osszeg=25
```

**Tipp:** indulj ki az első elemből; bejárás `for` vagy `for...of`-fal.

---

## 3) FizzBuzz+ – elágazások és ciklus

**Cél:** összetett feltételkezelés.

**Feladat:** 1-től 30-ig írd ki a számokat, de:
- ha osztható **3-mal** → `Fizz`
- ha osztható **5-tel** → `Buzz`
- ha mindkettővel → `FizzBuzz`
- egyébként a számot

**Részlet kimenet:**
```
1
2
Fizz
4
Buzz
...
FizzBuzz
...
```

**Tipp:** a „mindkettővel” ellenőrzést tedd **legelőre**.

---

## 4) Palindrom ellenőrző – string műveletek

**Cél:** string-kezelés, függvényírás.

**Feladat:** Írj függvényt `isPalindrom(szoveg)`, ami `true`-val tér vissza, ha a szöveg palindrom (visszafelé is ugyanaz, pl. „geeg”), különben `false`.

**Példa:**
```
isPalindrom("geeg") → true
isPalindrom("alma") → false
```

**Tipp:** alakítsd kisbetűssé, távolítsd el a szóközöket, majd hasonlítsd össze a megfordított változattal.

---

## 5) Tömb statisztika – átlag, párosak száma

**Cél:** tömb bejárása, feltételek, számítások.

**Feladat:** Egy szám tömbre számold ki az **átlagot** (két tizedesre kerekítve) és a **páros elemek számát**.

**Bemenet:**
```js
const arr = [10, 15, 20, 21, 22];
```

**Elvárt kimenet:**
```
atlag=17.60, paros_db=3
```

**Tipp:** `toFixed(2)` vagy `Math.round(x*100)/100`.

---

## 6) Gyakoriság-számláló – objektum, for...of

**Cél:** objektum mint számláló (map), iterálás.

**Feladat:** Írj függvényt `gyakorisag(szoveg)`, ami visszaad egy objektumot, ahol a kulcsok karakterek, az értékek az előfordulások száma.

**Példa:**
```
gyakorisag("abac") → { a: 2, b: 1, c: 1 }
```

**Tipp:** ha a kulcs még nincs az objektumban, kezdd 0-ról.

---

## 7) Egyedi elemek – Set vagy objektum

**Cél:** duplikátumok kiszűrése.

**Feladat:** Írj függvényt `egyedi(arr)`, ami visszaadja a tömb egyedi elemeit **eredeti sorrendben**.

**Példa:**
```
egyedi([1,1,2,3,3,3,2,4]) → [1,2,3,4]
```

**Tipp:** használhatsz `Set`-et vagy ellenőrizheted manuálisan, hogy már benne van-e a kimeneti tömbben.

---

## 8) Bevásárlókosár – összegzés, map/filter/reduce

**Cél:** objektumtömbök feldolgozása.

**Feladat:** Adott egy kosár tömb, benne tételekkel: `nev`, `ar`, `db`. Számold ki a **bruttó végösszeget** 27% áfával. A negatív vagy 0 db-os tételeket **szűrd ki**.

**Bemenet:**
```js
const kosar = [
  { nev: "Alma", ar: 120, db: 2 },
  { nev: "Kenyer", ar: 600, db: 1 },
  { nev: "Korte", ar: 300, db: 0 }, // szűrd ki
];
```

**Elvárt kimenet:**
```
vegosszeg_brutto= ? Ft
```

**Tipp:** `filter` → `map` (nettó sorár) → `reduce` (összeg), majd `* 1.27` és kerekítés.

---

## 9) Mini-kalkulátor függvény – paraméterezés

**Cél:** függvények, elágazás.

**Feladat:** Írj függvényt `calc(a, b, muvelet)`, ahol `muvelet` lehet: `"+"`, `"-"`, `"*"`, `"/"`. Hibakezelés: nullával osztás esetén írj hibaüzenetet és térj vissza `null`-lal.

**Példák:**
```
calc(10, 5, "+") → 15
calc(10, 0, "/") → null  (és konzolra: „Nem lehet nullával osztani!”)
```

**Tipp:** `switch (muvelet) { ... }` tiszta megoldás.

---

## 10) Parancssori ToDo (mini projekt) – tömb + objektum + függvények

**Cél:** kisebb program felépítése több függvényből, állapotkezelés tömbben.

**Feladat:** Készíts egy egyszerű ToDo-kezelőt konzolra. Legyen 4 funkció:  
- `hozzaad(cim)` – új teendő hozzáadása (objektumként: `{ id, cim, kesz: false }`)  
- `listaz()` – kilistázza a teendőket sorszámmal és státusszal  
- `kesz(id)` – beállítja készre az adott teendőt  
- `torol(id)` – törli az adott teendőt

**Minta futtatás:**
```
--- TODO ---
1. [ ] Bevásárlás
2. [x] Edzés
Új teendő felvéve: „Fizetés”
Készre állítva: #1
Törölve: #2
```

**Tipp:** tárold a teendőket egy tömbben; az `id` lehet futó sorszám. Írj külön függvényt mindegyik műveletre.

---

# Hibakeresési (debugging) tippek minden feladathoz

- Írj **közbenső `console.log`**-okat: mit vársz és mit kapsz valójában?  
- Ha elakadsz, **izoláld** a problémát egy mini-példába (új fájl, 5–10 sor).  
- Használd a **VS Code breakpointokat** (`F5` debug), nézd a **Variables** és **Watch** paneleket.  
- Ha `undefined`-ot kapsz, logold le, **hol** veszik el az érték.  
- Készíts kis **segédfüggvényeket** – könnyebb tesztelni és hibát keresni.

---

## Extra: javasolt fájlszerkezet

```
gyakorlo/
  feladat01.js
  feladat02.js
  ...
  feladat10.js
```

Minden fájl önállóan futtatható (`node feladat01.js`). Így könnyebb fókuszálni a megoldásra és lépésenként haladni.

Jó munkát, és sok sikert! 🚀
