<p align="center">
  <img src="https://engeto.cz/wp-content/uploads/2019/01/engeto-square.png" width="200" height="200">
</p>

# Java - 3. lekce

## Co bychom měli mít hotové

 - Po dvou hodinách už umíme pracovat ve vývojovém prostředí, umíme vytvořit projekt, spustit program a základy debugování
 
 - Umíme pracovat s proměnnými, víme jak definovat různé typy, jak přiřadit hodnotu do proměnné

 - Měli bychom vědět jak definovat vlastní třídu včetně proměnných, konstruktorů a metod 
 
 - Měli bychom znát základní operátory a umět z nich sestavit výraz

## Co nás čeká

- [Podmínky (if/else, switch)](#podmínky-ifelse-switch)
- [Pole (Array)](#pole-array)
- [Cykly (forEach, for, while)](#cykly-foreach-for-while)
- [Základy Kolekcí (List)](#zaklady-kolekci-list)

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

Zatím jsme se naučili, že počítač vykoná všechny příkazy v pořádí v jakém jsou v programu napsané. Často to ale není dostatečné a je potřeba vykonat dvě rozdílné části programu podle situace. K tomuto slouží podmíněné príkazy uvozené pomocí klíčových slov `if`, `else`.

Podmíněný příkaz si můžeme představit jako výhybku na kolejích. Podle směru přehození výhybky pokračujeme buď přímo, nebo projedeme „oklikou“ přes několik příkazů navíc. Na konci se běh vlakové trati zase spojí.

### Podmínka `if`

#### Podmínka s jedním příkazem
Nejjednodušší možný zápis (ale značne riskantní) je tento:
```
if (vyraz) příkaz;
```

Pozor, zkuste se zamyslet jaké příkazy se vykonají v případě, že podmínka je splněna a jaké v případě, že není?
```
if (vyraz)
    příkaz;
dalšíPříkaz;
```

výraz == true: příkaz; dalšíPříkaz;
výraz == false: dalšíPříkaz;

#### Podmínka s blokem příkazů
```
if (vyraz) {
    příkaz;
    dalšíPříkaz;
}
```

#### Podmínka s alternativní cestou `else`
Pokud chceme vykonat různé příkazy v obou případech, tak můžeme použít klíčové slovo `else`

```
if (vyraz) {
    příkaz;
    dalšíPříkaz;
} else {
    jinýPříkaz;
    dalšíPříkaz;
}
```

```
if (vyraz) {
    příkaz;
    dalšíPříkaz;
} else if (vyraz 2) {
    jinýPříkaz;
    dalšíPříkaz;
}
```

```
if (vyraz) {
    příkaz;
    dalšíPříkaz;
} else if (vyraz 2) {
    jinýPříkaz;
    dalšíPříkaz;
} else {
    dalšíPříkaz;
}
```


```
if (vyraz) {
    if (vyraz 2) {
        příkaz;
    } else {
        jinýPříkaz;
    }
} else {
    dalšíPříkaz;
}
```

### Jak na FizzBuzz?

Jak teď můžeme vylepšit FizzBuzz? Už umíme metodu se vstupním parametrem a výsledkem a teď jsme se naučili podmínky. Když to spojíme dohromady, tak máme řešení, které je o krok lepší.

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

### Podmíněne přirazení `výraz ? truePříkaz: falsePříkaz;`

V některých situacích potřebuje přiřadit dvě různé hodnoty do proměnné na základě podmínky. Pokud je to relativně jednoduchý výraz, tak je možné `if - else` nahradit zkráceným zápisem pomocí `?` a `:`.

```
String promenna = "Yes";
String vysledek = (promenna == "Yes")? "Ano":"Ne";
```

### Jak na výrazy

### Složené výrazy

#### AND - `(... && ...)`
```
if (true && false){
    //
}
```
#### OR - `(... || ...)`
```
if (true || false){
    //
}
```
#### NOT - `(... || ...)`
```
if (!false){
    //
}
```

### Příklady 

#### 1. Slovní známka
Napište metodu, která na základě známky vrátí slovní výraz. 1: Výborně, 2: Chvalitebně, 3: Dobře, 4: Dostatečně, 5: Nedostatečně

#### 2. Přestupný rok
Napište metodu která vrátí boolean na základě toho, jesli daný rok je nebo není přestupný.


## Pole (Array)
Velmi často potřebujeme v programování pracovat se skupinou hodnot stejného typu. Přitom často nevíme, kolik těchto hodnot bude.

V Javě jsou 2 přístupy - pole a kolekce

Nejprve si vysvětlíme co je to jednoduché pole.

### Definice pole
Pole je proměnná, která uloží pevně definovaný počet prvků jednoho typu.

```
Integer[] pole;
```

### Definice pole dané velikosti
Při vytvoření instance pole je nutné specikovat velikost pole. Protože jakmile se jednou vytvoří, tak už nejde velikost změnit. Jenom vytvořit nové pole jiné velikosti a prvky do nového pole přesunout. 
```
Integer[] pole = new Integer[10];
```

### Definice pole z existujicích hodnot
Zjedenodušený zápis, pokud už máme instance prvků, které chcem mít v poli.
```
Integer[] pole = {1,2,3,4};
```

### Práce s polem
Pole je indexované od nuly. K prvnímu prvku tedy přistupujeme `pole[0]`

```
Integer[] pole = {1,2,3,4};
Integer hodnotaDruha = pole[1];
pole[2] = 5;
```

```
String[] poleTextu;
int velikostPole = 15;
poleTextu = new String[velikostPole];
```

### Pole objektů
```
class Uzivatel {
    String jmeno;
}

Uzivatel[] pole = new Uzivatel[10];

pole[0] = new Uzivatel();
pole[0].jmeno = "Honza";
```


### Příklady 
#### 1. Nevalidní pokusy - jiný typ do pole
Zkuste do pole typu `Integer[]` přiřadit objekt jiného typu.
#### 2. Nevalidní pokusy - mimo rozsah
Zkuste do pole `Integer[] pole = new Integer[10]` dát prvek na devátou, desátou a jedenáctou pozici.

## Cykly (forEach, for, while)


### for 

Syntaxe; `for (inicializace; podmínka; příkazPo) příkaz;`

```
for (int i = 0; i < 10; i++){
    System.out.println(i);
}
```

### for cyklus nad polem pomocí indexu

```
Integer[] pole = new Integer[] {1,2,3}
for (int i = 0; i < pole.length; i++){
    System.out.println(pole[i]);
}
```

### for each
```
Integer[] pole = {1,2,3}
for (Integer i: pole){
    System.out.println(i);
}
```
   
### while 
```
int i = 0;
while (i < 10){
    i = i + 1; // nebo i++;
    System.out.println(i);
}
```

### for each pomocí Stream API
```
import java.util.Arrays;

Integer[] pole = {1,2,3,4};
Arrays.stream(pole).forEach(i -> { System.out.println(i); });
    
```

### Jak na FizzBuzz?

Teď už umíme všechno potřebné, umíme cyklus, podmínku i metodu. Konečně můžeme nahradit ručně rozkopírované volání od jedné do sta voláním v cyklu. 

```
class Main {
  public static void main(String[] args) {
    for (int i = 1; i <= 100; i++) {
      System.out.println(spocitejFizzBuzz(i));
    }
  }

  static String spocitejFizzBuzz(int i){
    if (i % 15 == 0 ){
        return "FizzBuzz";
    }
    if (i % 5 == 0 ){
        return "Buzz";
    }
    if (i % 3 == 0 ){
        return "Fizz";
    }
    return String.valueOf(i);  
  }
}
```

https://repl.it/@LukasHorak/FizzBuzzForCycle#Main.java

### Příklady 
#### 1. Řada
Napiště program, který do pole uloží čísla prvních 8 čísel Fibbonaciho řady 0,1,1,2,3,5,8,13 a vypíše jenom sudá čísla v opačném pořadí.

## Zaklady Kolekcí (List)

