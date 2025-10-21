# JavaScript operátorok és kifejezések

A programozásban gyakran végzünk **műveleteket**: összeadunk számokat, vizsgálunk feltételeket vagy éppen logikai kapcsolatokat hozunk létre.  
Ezekhez az eszközeink az **operátorok** és **kifejezések**.

Ebben a fejezetben megnézzük, hogyan működnek a különféle operátorok, mit jelentenek, és hogyan tudod őket hatékonyan használni a programodban.

---

## Mi az az operátor?

Az operátor egy **szimbólum vagy kulcsszó**, ami egy műveletet hajt végre az adatokon (operandusokon).  
Egy példa már ismerős lehet:

```js
let eredmeny = 5 + 3;
```
Itt a `+` jel az **operátor**, a `5` és `3` pedig az **operandusok**.  
A kifejezés eredménye `8` lesz.

---

## Mi az a kifejezés?

A kifejezés (expression) olyan kódrészlet, ami **értéket ad vissza**.

Például:
```js
2 + 3        // ez is egy kifejezés
"Hello" + " Világ" // ez is
let a = 10;  // itt a = jel jobb oldala egy kifejezés
```

Másképp fogalmazva: bármi, ami **eredményez valamit**, az kifejezés.

---

## Operátorok fajtái

A JavaScriptben rengeteg operátor van, de kategóriákba sorolhatók:

| Kategória | Példa | Mit csinál |
|------------|--------|------------|
| Aritmetikai | `+`, `-`, `*`, `/`, `%`, `**` | Matematikai műveletek |
| Összehasonlító | `==`, `===`, `!=`, `>`, `<`, `>=`, `<=` | Értékek összehasonlítása |
| Logikai | `&&`, `||`, `!` | Logikai kapcsolatokat vizsgál |
| Értékadó | `=`, `+=`, `-=`, `*=`, `/=`, `%=` | Értéket rendel egy változóhoz |
| Típusellenőrző | `typeof`, `instanceof` | Típusok vizsgálata |
| Egyéb | `?:`, `,`, `delete`, `in`, `void` | Speciális esetek |

---

## 1. Aritmetikai operátorok

Az alap matematikai műveletek ugyanúgy működnek, mint bármely más nyelvben.

| Operátor | Jelentés | Példa | Eredmény |
|-----------|-----------|--------|----------|
| `+` | Összeadás | `5 + 3` | 8 |
| `-` | Kivonás | `10 - 4` | 6 |
| `*` | Szorzás | `6 * 7` | 42 |
| `/` | Osztás | `20 / 5` | 4 |
| `%` | Maradékos osztás (modulo) | `10 % 3` | 1 |
| `**` | Hatványozás | `2 ** 3` | 8 |

**Példa:**
```js
let x = 10;
let y = 3;

console.log(x + y); // 13
console.log(x % y); // 1
```

---

### Összefűzés (Concatenation)

Ha az egyik operandus **string**, akkor a `+` **nem összead**, hanem **összefűz**:

```js
let szoveg = "Hello " + "Világ";
console.log(szoveg); // Hello Világ
```

Ha szám és szöveg keveredik, a JavaScript **stringgé alakítja** az egészet:

```js
console.log("5" + 5); // "55"
```

---

### Növelés és csökkentés

| Operátor | Jelentés | Példa | Eredmény |
|-----------|-----------|--------|----------|
| `++` | Növelés 1-gyel | `x++` | x = x + 1 |
| `--` | Csökkentés 1-gyel | `x--` | x = x - 1 |

```js
let szam = 10;
szam++;
console.log(szam); // 11
```

**Előjelentés és utójelentés különbsége:**

```js
let a = 5;
console.log(++a); // 6 (előbb növel, aztán kiír)
console.log(a++); // 6 (előbb kiír, aztán növel)
console.log(a);   // 7
```

---

## 2. Összehasonlító operátorok

Az összehasonlító operátorok logikai (true/false) értéket adnak vissza.

| Operátor | Jelentés | Példa | Eredmény |
|-----------|-----------|--------|----------|
| `==` | Egyenlőség (típuskonverzióval) | `"5" == 5` | true |
| `===` | Szigorú egyenlőség | `"5" === 5` | false |
| `!=` | Nem egyenlő | `10 != 5` | true |
| `!==` | Szigorúan nem egyenlő | `"5" !== 5` | true |
| `>` | Nagyobb mint | `8 > 5` | true |
| `<` | Kisebb mint | `3 < 7` | true |
| `>=` | Nagyobb vagy egyenlő | `5 >= 5` | true |
| `<=` | Kisebb vagy egyenlő | `4 <= 2` | false |

**Tipp:** mindig **`===`** és **`!==`** operátorokat használd, hogy elkerüld a típuskonverziós hibákat.

```js
console.log(0 == false);  // true (mert a JS átalakítja)
console.log(0 === false); // false (különböző típusok)
```

---

## 3. Logikai operátorok

A logikai operátorok **feltételek kombinálására** szolgálnak.

| Operátor | Jelentés | Példa | Eredmény |
|-----------|-----------|--------|----------|
| `&&` | ÉS (AND) | `true && false` | false |
| `||` | VAGY (OR) | `true || false` | true |
| `!` | NEM (NOT) | `!true` | false |

**Példa:**
```js
let kor = 20;
let vanJogsi = true;

if (kor >= 18 && vanJogsi) {
  console.log("Vezethet!");
} else {
  console.log("Nem vezethet.");
}
```

**Tipp:**  
A `&&` és `||` **rövidzáras kiértékelést** használ:  
- ha az első feltétel már elég az eredményhez, a másodikat nem vizsgálja tovább.

```js
false && console.log("Ez nem fut le");
true || console.log("Ez sem fut le");
```

---

## 4. Értékadó operátorok

A legegyszerűbb az `=` – ezzel adunk értéket egy változónak.

```js
let x = 10;
```

De vannak **összetett értékadók**, amik rövidítik a kódot:

| Operátor | Jelentés | Rövidítés |
|-----------|-----------|------------|
| `+=` | Összeadás és értékadás | `x += 5` ⇔ `x = x + 5` |
| `-=` | Kivonás és értékadás | `x -= 3` ⇔ `x = x - 3` |
| `*=` | Szorzás és értékadás | `x *= 2` ⇔ `x = x * 2` |
| `/=` | Osztás és értékadás | `x /= 4` ⇔ `x = x / 4` |
| `%=` | Maradékos osztás | `x %= 3` ⇔ `x = x % 3` |

**Példa:**
```js
let pont = 10;
pont += 5;  // 15
pont -= 3;  // 12
console.log(pont);
```

---

## 5. Típusellenőrző operátorok

### typeof

A `typeof` segítségével megnézheted, milyen típusú egy érték.

```js
console.log(typeof 42); // "number"
console.log(typeof "Hello"); // "string"
console.log(typeof true); // "boolean"
```

### instanceof

Ezzel megvizsgálhatod, hogy egy objektum egy adott típus példánya-e.

```js
let datum = new Date();
console.log(datum instanceof Date); // true
```

---

## 6. Feltételes (ternary) operátor

A ternary (`?:`) operátor egy **rövidített if-else** forma.

```js
let kor = 20;
let jogosultsag = (kor >= 18) ? "Felnőtt" : "Kiskorú";
console.log(jogosultsag); // Felnőtt
```

Ez a szerkezet gyakran helyettesít egy rövid `if-else` blokkot.  
Hasznos, ha rövid döntést kell hozni egy sorban.

---

## 7. Egyéb operátorok

| Operátor | Funkció | Példa |
|-----------|-----------|--------|
| `,` | Több kifejezés egymás után | `(a = 1, b = 2, a + b)` |
| `delete` | Objektum tulajdonság törlése | `delete obj.nev` |
| `in` | Ellenőrzi, van-e kulcs az objektumban | `"nev" in obj` |
| `void` | Kifejezés lefuttatása, de undefined visszaadás | `void(0)` |

---

## Operátorok precedenciája (műveleti sorrend)

A JavaScript, mint a matematika, **bizonyos sorrendben** hajtja végre a műveleteket.

| Sorrend | Operátorok | Példa |
|----------|-------------|--------|
| 1 | `()` zárójelek | `(2 + 3) * 4` |
| 2 | `++`, `--` | `x++` |
| 3 | `*`, `/`, `%` | `10 / 2 * 3` |
| 4 | `+`, `-` | `5 + 3 - 2` |
| 5 | Összehasonlítók | `>`, `<`, `>=`, `<=` |
| 6 | Egyenlőség | `==`, `===`, `!=`, `!==` |
| 7 | Logikai ÉS (`&&`) | `true && false` |
| 8 | Logikai VAGY (`||`) | `true || false` |
| 9 | Értékadás (`=`) | `x = 5` |

**Tipp:** mindig használj zárójeleket, ha nem vagy biztos a sorrendben – olvashatóbb is lesz.

---

## Gyakori hibák

⚠️ `"5" + 5` → `"55"` (összefűzés, nem összeadás!)  
⚠️ `0 == false` → `true`, de `0 === false` → `false`  
⚠️ `null >= 0` → `true`, mert konvertálja a típust  
⚠️ `NaN === NaN` → `false`, mert a NaN semmivel sem egyenlő

---

## Tippek

💡 Használd a `===` és `!==` operátorokat, hogy elkerüld a típuskonverziós hibákat.  
💡 Használj zárójeleket, ha bonyolult kifejezéseket írsz.  
💡 Kerüld, hogy szövegeket és számokat keverj matematikai műveletekben.  
💡 A ternary operátor remek eszköz rövid döntésekhez.  

---

## Összefoglalás

- Az **operátorok** műveleteket végeznek az értékeken.  
- A **kifejezések** mindig valamilyen értéket adnak vissza.  
- Ismerd meg a különbséget a `==` és `===` között.  
- A logikai operátorok kombinálják a feltételeket.  
- Az értékadó és aritmetikai operátorokat együtt is használhatod rövidítve.  
- A zárójelek segítenek a műveletek sorrendjének megértésében.  

A következő fejezetben belevágunk a **feltételek és elágazások** világába – azaz megtanuljuk, hogyan dönt a program különböző helyzetekben.
