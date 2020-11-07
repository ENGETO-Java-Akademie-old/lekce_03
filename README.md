<p align="center">
  <img src="https://engeto.cz/wp-content/uploads/2019/01/engeto-square.png" width="200" height="200">
</p>

# Java - 3. lekce

## Co bychom měli mít hotové

 - Po dvou hodinách už umíme pracovat ve vývojovém prostředí, uníme vytvořit projekt, spustit program a základy debugování
 
 - Umíme pracovat s proměnými, víme jak definovat různé typy, jak přiřadit hodnotu do proměnné

 - Měli bychom vědět jak definovat vlastní třídu včetně proměnných, kontruktorů a metod 
 
 - Měli bychom znát základní operátory a umět z nich sestavit výraz

## Co nás čeká

- [Podminky (if/else, switch)](#podminky-if-else-switch)
- [Pole (Array)](#pole-array)
- [Cykly (forEach, for, while)](#cykly-foreach-for-while)
- [Zaklady Kolekci (List)](#zaklady-kolekci-list)
- [Kolekce (Ruzne implementace Listu, Map, Set)](#kolekce-ruzne-implementace-listu-map-set)

## Motivace příkladem

Jedna ze základních motivací při vývoji softwaru je minimalizace manuální práce a snaha vyhnout se copy&paste. V této lekci si celý koncept ukážeme na jednom z nejzákladnějších příkladů - Fizz Buzz.

## Zadání Fizz Buzz

Počítejte od 1 do 100 a při každém kroku vypiště číslo daného kroku. Ale v případě, že je číslo dělitelné třemi, tak napište místo čísla Fizz. Pokud je dělitelné pěti, tak místo čísla vypište Buzz. A pokud je dělitelní třemi a pěti zároveň, tak FizzBuzz.

```
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
FizzBuzz
16
...
```

Po dvou lekcích už máme dostatek znalostí napsat velice naivní implementaci. Zkuste se zamyslet co potřebujeme na splnění takového úkolu?

```
class Main {
  public static void main(String[] args) {
    System.out.println(1);
    System.out.println(2);
    System.out.println(Fizz);
    System.out.println(4);
    System.out.println(Buzz);
    System.out.println(Fizz);
    System.out.println(7);
    System.out.println(8);
    System.out.println(Fizz);
    System.out.println(Buzz);
    System.out.println(11);
    System.out.println(Fizz);
    System.out.println(13);
    System.out.println(14);
    System.out.println(FizzBuzz);
    System.out.println(16);
    System.out.println(17);
    System.out.println(Fizz);
    System.out.println(19);
    System.out.println(Buzz);
    System.out.println(Fizz);
    System.out.println(22);
    System.out.println(23);
    System.out.println(Fizz);
    System.out.println(Buzz);
    System.out.println(26);
    System.out.println(Fizz);
    System.out.println(28);
    System.out.println(29);
    System.out.println(FizzBuzz);
    System.out.println(31);
    System.out.println(32);
    System.out.println(Fizz);
    System.out.println(34);
    System.out.println(Buzz);
    System.out.println(Fizz);
    System.out.println(37);
    System.out.println(38);
    System.out.println(Fizz);
    System.out.println(Buzz);
    System.out.println(41);
    System.out.println(Fizz);
    System.out.println(43);
    System.out.println(44);
    System.out.println(FizzBuzz);
    System.out.println(46);
    System.out.println(47);
    System.out.println(Fizz);
    System.out.println(49);
    System.out.println(Buzz);
    System.out.println(Fizz);
    System.out.println(52);
    System.out.println(53);
    System.out.println(Fizz);
    System.out.println(Buzz);
    System.out.println(56);
    System.out.println(Fizz);
    System.out.println(58);
    System.out.println(59);
    System.out.println(FizzBuzz);
    System.out.println(61);
    System.out.println(62);
    System.out.println(Fizz);
    System.out.println(64);
    System.out.println(Buzz);
    System.out.println(Fizz);
    System.out.println(67);
    System.out.println(68);
    System.out.println(Fizz);
    System.out.println(Buzz);
    System.out.println(71);
    System.out.println(Fizz);
    System.out.println(73);
    System.out.println(74);
    System.out.println(FizzBuzz);
    System.out.println(76);
    System.out.println(77);
    System.out.println(Fizz);
    System.out.println(79);
    System.out.println(Buzz);
    System.out.println(Fizz);
    System.out.println(82);
    System.out.println(83);
    System.out.println(Fizz);
    System.out.println(Buzz);
    System.out.println(86);
    System.out.println(Fizz);
    System.out.println(88);
    System.out.println(89);
    System.out.println(FizzBuzz);
    System.out.println(91);
    System.out.println(92);
    System.out.println(Fizz);
    System.out.println(94);
    System.out.println(Buzz);
    System.out.println(Fizz);
    System.out.println(97);
    System.out.println(98);
    System.out.println(Fizz);
    System.out.println(Buzz);
  }
}
```
https://repl.it/@LukasHorak/FizzBuzzCopyPaste#Main.java

## Podmínky (if/else, switch)

```
if (vyraz) {
    //
}
```

```
if (vyraz) {
    //
} else {
    
}
```

```
if (vyraz) {
    //
} else if (vyraz 2) {
    //
}
```

```
if (vyraz) {
    //
} else if (vyraz 2) {
    //
} else {
    //
}
```


```
if (vyraz) {
    if (vyraz 2) {
        //
    } else {
        //
    }
} else {
    //
}
```

### Jak na FizzBuzz?

Jak teď můžeme vylepšit FizzBuzz? Už umíme metodu se vstupním proměnou a výsledkem a teď jsme se naučili podmínky. Když to spojíme dohromady, tak máme řešení, které je o krok lepší.

```
class Main {
  public static void main(String[] args) {
    System.out.println(calculateFizzBuzz(1));
    System.out.println(calculateFizzBuzz(2));
    System.out.println(calculateFizzBuzz(3));
    System.out.println(calculateFizzBuzz(4));
    System.out.println(calculateFizzBuzz(5));
    System.out.println(calculateFizzBuzz(6));
    System.out.println(calculateFizzBuzz(7));
    System.out.println(calculateFizzBuzz(8));
    System.out.println(calculateFizzBuzz(9));
    System.out.println(calculateFizzBuzz(10));
    System.out.println(calculateFizzBuzz(11));
    System.out.println(calculateFizzBuzz(12));
    System.out.println(calculateFizzBuzz(13));
    System.out.println(calculateFizzBuzz(14));
    System.out.println(calculateFizzBuzz(15));
    System.out.println(calculateFizzBuzz(16));
    System.out.println(calculateFizzBuzz(17));
    System.out.println(calculateFizzBuzz(18));
    System.out.println(calculateFizzBuzz(19));
    System.out.println(calculateFizzBuzz(20));
    System.out.println(calculateFizzBuzz(21));
    System.out.println(calculateFizzBuzz(22));
    System.out.println(calculateFizzBuzz(23));
    System.out.println(calculateFizzBuzz(24));
    System.out.println(calculateFizzBuzz(25));
    System.out.println(calculateFizzBuzz(26));
    System.out.println(calculateFizzBuzz(27));
    System.out.println(calculateFizzBuzz(28));
    System.out.println(calculateFizzBuzz(29));
    System.out.println(calculateFizzBuzz(30));
    System.out.println(calculateFizzBuzz(31));
    System.out.println(calculateFizzBuzz(32));
    System.out.println(calculateFizzBuzz(33));
    System.out.println(calculateFizzBuzz(34));
    System.out.println(calculateFizzBuzz(35));
    System.out.println(calculateFizzBuzz(36));
    System.out.println(calculateFizzBuzz(37));
    System.out.println(calculateFizzBuzz(38));
    System.out.println(calculateFizzBuzz(39));
    System.out.println(calculateFizzBuzz(40));
    System.out.println(calculateFizzBuzz(41));
    System.out.println(calculateFizzBuzz(42));
    System.out.println(calculateFizzBuzz(43));
    System.out.println(calculateFizzBuzz(44));
    System.out.println(calculateFizzBuzz(45));
    System.out.println(calculateFizzBuzz(46));
    System.out.println(calculateFizzBuzz(47));
    System.out.println(calculateFizzBuzz(48));
    System.out.println(calculateFizzBuzz(49));
    System.out.println(calculateFizzBuzz(50));
    System.out.println(calculateFizzBuzz(51));
    System.out.println(calculateFizzBuzz(52));
    System.out.println(calculateFizzBuzz(53));
    System.out.println(calculateFizzBuzz(54));
    System.out.println(calculateFizzBuzz(55));
    System.out.println(calculateFizzBuzz(56));
    System.out.println(calculateFizzBuzz(57));
    System.out.println(calculateFizzBuzz(58));
    System.out.println(calculateFizzBuzz(59));
    System.out.println(calculateFizzBuzz(60));
    System.out.println(calculateFizzBuzz(61));
    System.out.println(calculateFizzBuzz(62));
    System.out.println(calculateFizzBuzz(63));
    System.out.println(calculateFizzBuzz(64));
    System.out.println(calculateFizzBuzz(65));
    System.out.println(calculateFizzBuzz(66));
    System.out.println(calculateFizzBuzz(67));
    System.out.println(calculateFizzBuzz(68));
    System.out.println(calculateFizzBuzz(69));
    System.out.println(calculateFizzBuzz(70));
    System.out.println(calculateFizzBuzz(71));
    System.out.println(calculateFizzBuzz(72));
    System.out.println(calculateFizzBuzz(73));
    System.out.println(calculateFizzBuzz(74));
    System.out.println(calculateFizzBuzz(75));
    System.out.println(calculateFizzBuzz(76));
    System.out.println(calculateFizzBuzz(77));
    System.out.println(calculateFizzBuzz(78));
    System.out.println(calculateFizzBuzz(79));
    System.out.println(calculateFizzBuzz(80));
    System.out.println(calculateFizzBuzz(81));
    System.out.println(calculateFizzBuzz(82));
    System.out.println(calculateFizzBuzz(83));
    System.out.println(calculateFizzBuzz(84));
    System.out.println(calculateFizzBuzz(85));
    System.out.println(calculateFizzBuzz(86));
    System.out.println(calculateFizzBuzz(87));
    System.out.println(calculateFizzBuzz(88));
    System.out.println(calculateFizzBuzz(89));
    System.out.println(calculateFizzBuzz(90));
    System.out.println(calculateFizzBuzz(91));
    System.out.println(calculateFizzBuzz(92));
    System.out.println(calculateFizzBuzz(93));
    System.out.println(calculateFizzBuzz(94));
    System.out.println(calculateFizzBuzz(95));
    System.out.println(calculateFizzBuzz(96));
    System.out.println(calculateFizzBuzz(97));
    System.out.println(calculateFizzBuzz(98));
    System.out.println(calculateFizzBuzz(99));
    System.out.println(calculateFizzBuzz(100));
  }

  static String calculateFizzBuzz(int i){
    String vysledek = String.valueOf(i);
      if (i % 3 == 0 ){
        vysledek = "Fizz";
      }
      if (i % 5 == 0 ){
        vysledek = "Buzz";
      }
      if (i % 15 == 0 ){
        vysledek = "FizzBuzz";
      }
      return vysledek;
  }
}
```

https://repl.it/@LukasHorak/FizzBuzzIfElseOnly#Main.java

## Pole (Array)

## Cykly (forEach, for, while)

```
for (int i = 0; i < 10; i++){
    //
}
```

```
Integer[] pole = new Integer[] {1,2,3}
for (int i = 0; i < pole.length; i++){
    //
}
```

```
Integer[] pole = new Integer[] {1,2,3}

for (Integer i: pole){
    //
}
```

```
int i = 0;
while (i < 10){
    i = i + 1; // nebo i++;
    //
}
```

## Zaklady Kolekci (List)

## Kolekce (Ruzne implementace Listu, Map, Set)
