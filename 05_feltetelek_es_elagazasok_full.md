# JavaScript feltételek és elágazások (if, else, switch)

A programozás egyik legfontosabb eleme a **döntéshozás**.  
A programnak gyakran el kell döntenie, hogy egy adott feltétel igaz-e vagy hamis, és ez alapján különböző utakat kell bejárnia.  

Ebben a fejezetben megnézzük, hogyan tud a JavaScript **feltételeket vizsgálni** és **eltérő utasításokat végrehajtani**.

---

## Mi az a feltétel és elágazás?

Egy **feltétel** (condition) egy logikai kifejezés, ami `true` (igaz) vagy `false` (hamis) értéket ad vissza.  
Az **elágazás** (branching) pedig azt jelenti, hogy a program különböző utat választ attól függően, mi az eredmény.

**Példa:**

```js
let kor = 18;

if (kor >= 18) {
  console.log("Felnőtt vagy.");
} else {
  console.log("Még kiskorú vagy.");
}
```

Ha a feltétel (`kor >= 18`) igaz, a program az első ágat futtatja le, különben a másodikat.

---

## if szerkezet

Az `if` a legegyszerűbb elágazás. Csak akkor fut le a blokk, ha a feltétel igaz.

```js
if (feltetel) {
  // ha igaz
}
```

**Példa:**
```js
let esik = true;

if (esik) {
  console.log("Ne felejtsd el az esernyőt!");
}
```

Ha `esik` értéke `false`, a program nem ír ki semmit.

---

## if–else szerkezet

Az `else` ágat akkor használjuk, ha azt is meg akarjuk mondani, mi történjen, ha a feltétel hamis.

```js
let ido = 10;

if (ido < 12) {
  console.log("Jó reggelt!");
} else {
  console.log("Szép napot!");
}
```

Ha `ido` kisebb mint 12, az első ág fut le, egyébként a második.

---

## if – else if – else láncolás

Ha több különböző feltételt szeretnél vizsgálni egymás után, használj `else if` szerkezetet.

```js
let pont = 85;

if (pont >= 90) {
  console.log("Kitűnő!");
} else if (pont >= 70) {
  console.log("Jó munka!");
} else if (pont >= 50) {
  console.log("Sikeres vizsga.");
} else {
  console.log("Sikertelen.");
}
```

A program mindig **fentről lefelé** vizsgálja a feltételeket, és az első igaz ágnál megáll.

---

## Egymásba ágyazott if-ek

Az `if`-ek egymásba is ágyazhatók, ha bonyolultabb logikára van szükség.

```js
let bejelentkezett = true;
let admin = false;

if (bejelentkezett) {
  if (admin) {
    console.log("Üdvözöllek, admin!");
  } else {
    console.log("Üdvözöllek, felhasználó!");
  }
} else {
  console.log("Kérlek, jelentkezz be!");
}
```

**Tipp:** ha túl sok egymásba ágyazott `if` van, érdemesebb `switch` vagy külön függvény használata.

---

## Rövidített feltételek (ternary operátor)

A **ternary** (háromrészes) operátor egy rövid forma az `if–else` helyett.

```js
feltetel ? ha_igaz : ha_hamis
```

**Példa:**
```js
let kor = 20;
let uzenet = (kor >= 18) ? "Felnőtt vagy" : "Kiskorú vagy";
console.log(uzenet);
```

Ez teljesen ugyanazt csinálja, mint:
```js
if (kor >= 18) {
  uzenet = "Felnőtt vagy";
} else {
  uzenet = "Kiskorú vagy";
}
```

**Tipp:** rövid döntésekhez remek, de ha több feltétel van, maradj a hagyományos `if–else` szerkezetnél.

---

## switch szerkezet

Ha sok hasonló feltételt vizsgálsz (például több lehetséges értéket), akkor a `switch` szerkezet átláthatóbb.

**Szintaxis:**
```js
switch (kifejezés) {
  case érték1:
    // ha a kifejezés értéke érték1
    break;

  case érték2:
    // ha a kifejezés értéke érték2
    break;

  default:
    // ha egyik sem illik
}
```

**Példa:**
```js
let nap = "kedd";

switch (nap) {
  case "hétfő":
    console.log("A hét első napja.");
    break;
  case "kedd":
    console.log("Már túl az első napon!");
    break;
  case "szerda":
    console.log("A hét közepe.");
    break;
  default:
    console.log("Ismeretlen nap.");
}
```

A `break` megakadályozza, hogy a program az összes alatta lévő ágat is lefuttassa.  
Ha szándékosan szeretnél több esetet ugyanúgy kezelni, **kihagyhatod a break-et**:

```js
let nap = "hétfő";

switch (nap) {
  case "hétfő":
  case "kedd":
  case "szerda":
    console.log("Hét eleje.");
    break;
  default:
    console.log("Hét vége.");
}
```

---

## Feltételek kombinálása logikai operátorokkal

Az `if` feltételekben logikai operátorokat (`&&`, `||`, `!`) is használhatsz.  
Így több feltételt is egyszerre ellenőrizhetsz.

**Példa:**
```js
let eletkor = 25;
let jogosultsag = true;

if (eletkor >= 18 && jogosultsag) {
  console.log("Vezethet!");
}
```

- `&&` → mindkét feltételnek igaznak kell lennie  
- `||` → elég, ha az egyik igaz  
- `!` → tagadás (az ellenkezőjét adja vissza)

```js
let diak = false;

if (!diak) {
  console.log("Nem diák.");
}
```

---

## Truthy és Falsy értékek a feltételekben

A JavaScript minden értéket „igaznak” (truthy) vagy „hamisnak” (falsy) értékel, ha logikai kontextusban szerepel.

### Falsy értékek:
- `false`
- `0`
- `""` (üres string)
- `null`
- `undefined`
- `NaN`

Minden más érték truthy.

**Példa:**
```js
if ("Hello") console.log("Igaz érték.");
if (0) console.log("Ez nem fut le.");
```

---

## Tipikus hibák

⚠️ Elfelejtett `break` a `switch`-ben → lefut az összes alatta lévő ág.  
⚠️ Egyenlőség helyett `=` (értékadás) → pl. `if (x = 5)` mindig igaz lesz!  
⚠️ Túl sok egymásba ágyazott `if` → olvashatatlan kód.  
⚠️ `"false"` (szövegként) **truthy**, tehát nem hamis!

---

## Tippek

💡 Használj `===` a feltételekben, hogy elkerüld a típuskonverziót.  
💡 Ha több hasonló értéket vizsgálsz, használd a `switch`-et.  
💡 Rövid döntéseknél jöhet a ternary `? :` forma.  
💡 A `!` (negáció) hasznos lehet értékek logikai megfordítására.  

---

## Összefoglalás

- Az `if` és `else` vezérli, mi történjen igaz vagy hamis feltételek esetén.  
- Az `else if` több különböző lehetőséget enged.  
- A `switch` tisztább, ha sok hasonló értéket vizsgálsz.  
- A ternary (`?:`) operátor rövidíti a kódot.  
- A logikai operátorokkal több feltételt is kombinálhatsz.  

A következő fejezetben megnézzük, **hogyan ismételhetünk meg műveleteket** a programban – jönnek a **ciklusok (for, while, do...while)**!
