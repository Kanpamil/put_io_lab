# System aukcyjny

## Wprowadzenie

Specyfikacja wymagań funkcjonalnych w ramach informatyzacji procesu sprzedaży produktów w oparciu o mechanizm aukcyjny. 

## Procesy biznesowe

---
<a id="bc1"></a>
### BC1: Sprzedaż aukcyjna 

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Opis:** Proces biznesowy opisujący sprzedaż za pomocą mechanizmu aukcyjnego. |

**Scenariusz główny:**
1. [Sprzedający](#ac1) wystawia produkt na aukcję. ([UC1](#uc1))
2. [Kupujący](#ac2) oferuje kwotę za produkt wyższą od aktualnie najwyższej oferty. ([BR1](#br1)) ([UC2](#uc2))
3. [Kupujący](#ac2) wygrywa aukcję ([BR2](#br2))([UC3](#uc3))
4. [Kupujący](#ac2) przekazuje należność Sprzedającemu. ([UC4](#uc4))
5. [Sprzedający](#ac1) przekazuje produkt Kupującemu.([UC5](#uc5))

**Scenariusze alternatywne:** 

2.A. Oferta Kupującego została przebita, a [Kupujący](#ac2) pragnie przebić aktualnie najwyższą ofertę.([UC6](#uc6))
* 2.A.1. Przejdź do kroku 2.

3.A. Czas aukcji upłynął i [Kupujący](#ac2) przegrał aukcję. ([BR2](#br2))([UC7](#uc7))
* 3.A.1. Koniec przypadku użycia.

---

## Aktorzy

<a id="ac1"></a>
### AC1: Sprzedający

Osoba oferująca towar na aukcji.

<a id="ac2"></a>
### AC2: Kupujący

Osoba chcąca zakupić produkt na aukcji.


## Przypadki użycia poziomu użytkownika

### Aktorzy i ich cele

[Sprzedający](#ac1):
* [UC1](#uc1): Wystawienie produktu na aukcję
* [UC5](#uc5): Przekazanie produktu


[Kupujący](#ac2)
* [UC2](#uc2): Zaoferowanie kwoty za produkt wyższej od aktualnie najwyższej oferty
* [UC3](#uc3) Finalizacja aukcji
* [UC4](#uc4): Przekazanie należności Sprzedającemu
* [UC5](#uc5) Przekazanie produktu

---
<a id="uc1"></a>
### UC1: Wystawienie produktu na aukcję

**Aktorzy:** [Sprzedający](#ac1)

**Scenariusz główny:**
1. [Sprzedający](#ac1) zgłasza do systemu chęć wystawienia produktu na aukcję.
2. System prosi o podanie danych produktu i ceny wywoławczej.
3. [Sprzedający](#ac1) podaje dane produktu oraz cenę wywoławczą.
4. System weryfikuje poprawność danych.
5. System informuje o pomyślnym wystawieniu produktu na aukcję.

**Scenariusze alternatywne:** 

4.A. Podano niepoprawne lub niekompletne dane produktu.
* 4.A.1. System informuje o błędnie podanych danych.
* 4.A.2. Przejdź do kroku 2.

---

<a id="uc2"></a>
### UC2: Zaoferowanie kwoty wyższej od aktualnie najwyższej oferty

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2), ...

**Scenariusz główny:**
1. [Kupujący](#ac2) zgłasza chęć złożenia oferty.
2. System prosi o podanie kwoty.
3. [Kupujący](#ac2) podaje kwote, którą jest gotów zapłacić
4. System weryfikuje czy kwota jest poprawna
5. System informuje o przekazaniu oferty

**Scenariusze alternatywne:** 

1.A. Podano niepoprawną kwotę
* 4.A.1. System informuje o błędnie przekazanej kwocie
* 4.A.2 Przejdź do kroku 2

---

<a id="uc3"></a>
### UC3: Finalizacja aukcji

**Aktorzy:**  [Kupujący](#ac2)

**Scenariusz główny:**
1. System informuje o zakończeniu aukcji
2. System informuje o zwycięstwie [Kupującego](#ac2), z najwyższą kwotą
3. System informuje o przegranej pozostałych [Kupujących]
4. System informuje [Sprzedającego]

---


<a id="uc4"></a>
### UC4: Przekazanie należności Sprzedającemu

**Aktorzy:**  [Kupujący](#ac2), [Sprzedający](#ac1)

**Scenariusz główny:**
1. System informuje o konieczności zapłaty
2. [Kupujący](#ac2) wybiera [metodę płatności](#bo4) i używa jej
3. System przekazuje pieniądze do [Sprzedającego](#ac1)

**Scenariusze alternatywne:** 

1.A. Płatność daną metodą nie udała się
* 2.A.1. System informuje o nieudanej próbie płatności
* 2.A.2 Przejdź do kroku 2
2.A. Wszystkie płatności nie udały się
    2.B.1 System kontaktuje się z innym [Kupującym](#ac2)


---
<a id="uc5"></a>
### UC5: Przekazanie produktu [Kupującemu](#ac2)

**Aktorzy:**  [Kupujący](#ac2), [Sprzedający](#ac1)

**Scenariusz główny:**
1. System informuje o konieczności przekazania produktu
2. [Kupujący](#ac2) wybiera metodę dostawy i podaje swoje [dane dostawy](#bo3)
3. System informuje [Sprzedającego](#ac1) jakiej metody dostawy użyć

**Scenariusze alternatywne:** 

1.A. Metoda dostarczenia jest niedostępna
* 2.A.1. System informuje o niedostępnej metodzie dostarczenia
* 2.A.2 Przejdź do kroku 2

---
## Obiekty biznesowe (inaczje obiekty dziedzinowe lub informatycjne)

### BO1: Aukcja

Aukcja jest formą zawierania transakcji kupna-sprzedaży, w której Sprzedający określa cenę wywoławczą produktu, natomiast Kupujący mogą oferować własną ofertę zakupu każdorazowo proponując kwotę wyższą od aktualnie oferowanej kwoty. Aukcja kończy się po upływie określonego czasu. Jeśli złożona została co najmniej jedna oferta zakupy produkt nabywa ten Kupujący, który zaproponował najwyższą kwotę. 

### BO2: Produkt

Fizyczny lub cyfrowy obiekt, który ma zostać sprzedany w ramach aukcji.

<a id="bo3"></a>

### BO3: Dane dostawy

Adres zamieszkania, na który ma zostać dostarczony przedmiot

<a id="bo4"></a>

### BO4: Metody płatności

Metoda płatności jest sposobem przekazania środków płatniczych między Kupującym, a Sprzedawcą, czyli

## Reguły biznesowe

<a id="br1"></a>

### BR1: Złożenie oferty

Złożenie oferty wymaga zaproponowania kwoty wyższej niż aktualnie oferowana o minimum 1,00 PLN.


<a id="br2"></a>

### BR2: Rozstrzygnięcie aukcji

Aukcję wygrywa ten z [Kupujący](#ac2)ch, który w momencie jej zakończenia (upłynięcia czasu) złożył najwyższą ofertę.

<a id="br3"></a>

### BR3: Branie udziału
Branie udziału w aukcji wymaga posiadania konta w systemie

<a id="br4"></a>

### BR4: Płatność
Płatność musi zostać wykonana w ciągu 7 dni od zakończenia licytacji

### BR5: Dostawa
Produkt musi zostać wysłany w ciągu 7 dni od finalizacji zapłaty



## Macierz CRUDL


| Przypadek użycia                                  | Aukcja | Produkt | ... |
| ------------------------------------------------- | ------ | ------- | --- |
| UC1: Wystawienia produktu na aukcję               |    C   |    C    | ... |
| ???                                               |  ...   |  ...    | ... |


