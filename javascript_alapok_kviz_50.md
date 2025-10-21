# JavaScript alapok – 50 kérdéses kvíz (10 témakör × 5 kérdés)

Minden kérdéshez **egy helyes válasz** tartozik. A végén megtalálod a **megoldókulcsot**.

---

## 1) Bevezetés

1. Melyik állítás igaz a JavaScriptre?
   - A) Előre fordított, erősen típusos nyelv
   - B) Értelmezett, dinamikus nyelv
   - C) Csak szerveroldalon fut
   - D) Nem futtatható Node.js-ben

2. Milyen szerepe van a JavaScriptnek egy weboldalon?
   - A) Szerkezet
   - B) Stílus
   - C) Működés / Interakció
   - D) Képek tömörítése

3. Ki hozta létre a JavaScriptet?
   - A) Linus Torvalds
   - B) Guido van Rossum
   - C) Brendan Eich
   - D) James Gosling

4. Melyik év jelzi az ES6 (ES2015) bevezetését?
   - A) 2009
   - B) 2012
   - C) 2015
   - D) 2018

5. Hol futtathatunk JavaScriptet?
   - A) Csak Chrome böngészőben
   - B) Minden modern böngészőben és Node.js-ben
   - C) Csak mobileszközökön
   - D) Csak szervereken

---

## 2) Változók és konstansok

6. Melyik kulcsszóval **nem** hozható létre változó modern JS-ben?
   - A) var
   - B) let
   - C) const
   - D) val

7. Mi igaz a `const`-ra?
   - A) Bármikor újra deklarálható
   - B) Értéke felülírható
   - C) Kötelező kezdőértéket adni
   - D) Nincs scope-ja

8. Mi a `let` scope-ja?
   - A) Globális
   - B) Függvény
   - C) Blokk
   - D) Modulfüggetlen

9. Mi történik ezzel a kóddal?
   ```js
   let x = 1;
   let x = 2;
   ```
   - A) 2 lesz az x értéke
   - B) Szintaktikai hiba
   - C) 1 marad az x
   - D) Runtime hiba

10. Melyik változónév érvénytelen?
    - A) _count
    - B) $osszeg
    - C) 2db
    - D) atlagErtek

---

## 3) Adattípusok és konverziók

11. Mi a `typeof null` eredménye?
    - A) "null"
    - B) "object"
    - C) "undefined"
    - D) "number"

12. Mit kapunk: `"5" + 5`?
    - A) 10
    - B) "10"
    - C) "55"
    - D) NaN

13. Mit ad vissza `Number("42a")`?
    - A) 42
    - B) "42"
    - C) NaN
    - D) 0

14. Melyik **falsy** érték?
    - A) "0"
    - B) []
    - C) 0
    - D) "false"

15. Melyik alakít szöveget számmá?
    - A) String()
    - B) Number()
    - C) Boolean()
    - D) typeof

---

## 4) Operátorok és kifejezések

16. Mi a különbség a `==` és `===` között?
    - A) Semmi
    - B) `===` típuskonverziót végez
    - C) `==` szigorúbb
    - D) `===` típusérzékeny összehasonlítás

17. Mi az `&&` operátor neve?
    - A) Vagy
    - B) És
    - C) Nem
    - D) XOR

18. Mi lesz az `x` értéke?
    ```js
    let x = 5;
    x += 3;
    ```
    - A) 3
    - B) 5
    - C) 8
    - D) 15

19. Mi az eredmény?
    ```js
    10 % 3
    ```
    - A) 0
    - B) 1
    - C) 2
    - D) 3

20. Mire jó a ternary operátor?
    - A) Ciklus írására
    - B) String összefűzésre
    - C) Rövid if–else-re
    - D) Modul importálásra

---

## 5) Feltételek és elágazások

21. Melyik kulcsszó **nem** tartozik az if-szerkezethez?
    - A) if
    - B) else
    - C) switch
    - D) else if

22. Mi történik, ha a `switch` ágból kihagyjuk a `break`-et?
    - A) Hiba keletkezik
    - B) Kilép a switch-ből
    - C) Továbbfut a következő case-ekre
    - D) Újraindul a program

23. Melyik igaz?
    - A) Az `if` feltétele csak boolean lehet
    - B) Minden érték truthy vagy falsy lehet kontextustól függően
    - C) Csak számok lehetnek a feltételekben
    - D) Az üres string truthy

24. Mi az eredmény?
    ```js
    if (0) { console.log("A"); } else { console.log("B"); }
    ```
    - A) "A"
    - B) "B"
    - C) Hiba
    - D) Nincs kiírás

25. Mit jelent a rövidzáras kiértékelés (`&&`, `||`)?
    - A) Mindig mindkét oldalt kiértékeli
    - B) Csak az első operandust nézi
    - C) Szükség esetén meg sem vizsgálja a másikat
    - D) Véletlenszerűen dönt

---

## 6) Ciklusok

26. Melyik ciklus fut le legalább egyszer?
    - A) for
    - B) while
    - C) do...while
    - D) mindegyik

27. Mi a hibás ebben?
    ```js
    for (let i = 0; i < 5; i--) { ... }
    ```
    - A) Nincs hiba
    - B) Soha nem lép be
    - C) Végtelen ciklus lehet
    - D) A `let` helytelen

28. Melyik ugrik ki a ciklusból?
    - A) skip
    - B) break
    - C) continue
    - D) stop

29. Melyik ugrik a **következő iterációra**?
    - A) break
    - B) continue
    - C) next
    - D) pass

30. Melyik való **tömb bejárására** elemenként?
    - A) for...in
    - B) for...of
    - C) switch
    - D) typeof

---

## 7) Függvények

31. Mit csinál a `return`?
    - A) Kiír a konzolra
    - B) Leállítja a programot
    - C) Visszaad értéket és befejezi a függvényt
    - D) Változót hoz létre

32. Mi az arrow function jele?
    - A) `->`
    - B) `=>`
    - C) `:=`
    - D) `>>`

33. Mi igaz az arrow function-ökre?
    - A) Saját `this`-ük van
    - B) Nincs saját `this`-ük
    - C) Mindig kell kapcsos zárójel
    - D) Nem lehet paraméterük

34. Mi a különbség a függvény deklaráció és kifejezés között?
    - A) Semmi
    - B) A deklaráció hoistingolódik
    - C) A kifejezés hoistingolódik
    - D) Mindkettő hoistingolódik

35. Mit ad vissza egy `return` nélküli függvény?
    - A) 0
    - B) ""
    - C) undefined
    - D) null

---

## 8) Tömbök

36. Mi a tömb első elemének indexe?
    - A) -1
    - B) 0
    - C) 1
    - D) 2

37. Melyik **nem** módosítja az eredeti tömböt?
    - A) slice
    - B) splice
    - C) sort
    - D) reverse

38. Mit csinál a `map()`?
    - A) Szűr
    - B) Minden elemből újat készít és visszaadja az új tömböt
    - C) Összegzi az elemeket
    - D) Rendez

39. Mit csinál a `filter()`?
    - A) Összegzi az elemeket
    - B) Csak a feltételnek megfelelő elemeket tartja meg
    - C) Új tömböt készít más értékekkel
    - D) Szöveggé alakít

40. Miért kell összehasonlító függvény számoknál a `sort()`-hoz?
    - A) Mert különben hibát dob
    - B) Mert alapból stringként hasonlít
    - C) Mert csak növekvő rendezést tud
    - D) Mert lassú

---

## 9) Objektumok

41. Mi a különbség a dot és a bracket notáció között?
    - A) Semmi
    - B) Bracket változó kulcsnevet is tud kezelni
    - C) Dot gyorsabb és mindig kötelező
    - D) Bracket csak számokra jó

42. Mit ad vissza `Object.keys(obj)`?
    - A) Az értékeket
    - B) A kulcs–érték párokat
    - C) A kulcsok tömbjét
    - D) A metódusokat

43. Hogyan másolsz **sekélyen** objektumot modern JS-ben?
    - A) `obj.copy()`
    - B) `Object.clone(obj)`
    - C) `{ ...obj }`
    - D) `new obj()`

44. Mit jelent az, hogy az objektumok referenciák?
    - A) Mindig másolással tárolódnak
    - B) Változóba téve ugyanarra a memóriára mutathatnak
    - C) Nem lehet őket módosítani
    - D) Csak számokat tárolnak

45. Mi a `this` tipikus jelentése objektum metódusában?
    - A) Globális objektum
    - B) Az aktuális objektum
    - C) Az aktuális függvény neve
    - D) `undefined`

---

## 10) Debugging

46. Mit csinál a `console.log`?
    - A) Megállítja a futást
    - B) Hibát dob
    - C) Kiír a konzolra
    - D) Fájlba ír

47. Mire jó a `debugger` utasítás?
    - A) Kitörli a változókat
    - B) Megállítja a futást a debuggerben
    - C) Újraindítja a programot
    - D) Leállítja a Node-ot

48. Melyik jelzi a VS Code-ban, hol áll meg a program?
    - A) Breakpoint (piros pont)
    - B) Bookmark (kék jel)
    - C) Comment
    - D) Lint warning

49. Mit jelent a `try...catch`?
    - A) Ciklus
    - B) Hibakezelés
    - C) Rendezés
    - D) Modul import

50. Melyik panel mutatja a hívási láncot (melyik függvény hívta melyiket) VS Code debug módban?
    - A) Problems
    - B) Explorer
    - C) Call Stack
    - D) Output

---

## Megoldókulcs

1:B, 2:C, 3:C, 4:C, 5:B,  
6:D, 7:C, 8:C, 9:B, 10:C,  
11:B, 12:C, 13:C, 14:C, 15:B,  
16:D, 17:B, 18:C, 19:B, 20:C,  
21:C, 22:C, 23:B, 24:B, 25:C,  
26:C, 27:C, 28:B, 29:B, 30:B,  
31:C, 32:B, 33:B, 34:B, 35:C,  
36:B, 37:A, 38:B, 39:B, 40:B,  
41:B, 42:C, 43:C, 44:B, 45:B,  
46:C, 47:B, 48:A, 49:B, 50:C
