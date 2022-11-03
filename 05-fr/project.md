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
2. [Kupujący](#ac2) oferuje kwotę za produkt wyższą od aktualnie najwyższej oferty. ([BR1](#br1))
3. [Kupujący](#ac2) wygrywa aukcję ([BR2](#br2))
4. [Kupujący](#ac2) przekazuje należność Sprzedającemu.
5. [Sprzedający](#ac1) przekazuje produkt Kupującemu.

**Scenariusze alternatywne:** 

2.A. Oferta Kupującego została przebita, a [Kupujący](#ac2) pragnie przebić aktualnie najwyższą ofertę.
* 2.A.1. Przejdź do kroku 2.

3.A. Czas aukcji upłynął i [Kupujący](#ac2) przegrał aukcję. ([BR2](#br2))
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
* [UC2](#uc2): Przekazanie produktu zwycięzcy aukcji
* [UC3](#uc3): Ustalenie ceny wywoławczej
* [UC4](#uc4): Zakończenie aukcji
* [UC5](#uc5): Wgranie opisu produktu


[Kupujący](#ac2)
* [BR1](#br1) zgłoszenie oferty wyższej od wszystkich innych
* [BR2](#br2) przekazanie należności sprzedającemu
* [BR3](#br3) Obejrzenie produktu

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

<a id="br1"></a>
### BR1: Złożenie oferty wyższej od inncyh

**Aktorzy:** [Kupujący](#br1)

**Scenariusz główny:**
1. [Kupujący](#br1) zgłasza chęć złożenia kontroferty
2. System prosi o podanie wysokości oferty
3. [Kupujący](#br1) podaje wysokość kontroferty
4. System weryfikuje poprawnośc danych
5. System informuje o pomyślnym złożeniu kontroferty. 

**Scenariusze alternatywne:** 

3.A. Podano za niską lub niepoprawną wysokość kontroferty
* 3.A.1. System informuje o błednej wartości kontroferty
* 3.A.2 Przejdź do kroku 2

---

<a id="br2"></a>
### BR2: Przekazanie należności sprzedającemu

**Aktorzy:** [Kupujący](#br1)

**Scenariusz główny:**
1. System prosi o podanie dancyh karty płatniczej
2. [Kupujący](#br1) podaje dane swojej karty płatniczej
3. System weryfikuje poprawnośc danych
4. System prosi kupującego o autoryzację płatności w aplikacji bankowej sprzedającego
5. Kupujący autoryzuje płatność w aplikacji bankowej 
6. System informuje o pomyślnej autoryzacji płatności. 

**Scenariusze alternatywne:** 

2.A. Podano niepełne lub niepoprawne dane
* 3.A.1. System informuje o błednie wprowadzoncyh danych
* 3.A.2 Przejdź do kroku 2

5.A Kupujący nie dokonał autoryzacji płatności
* 5.A.1 System informuje o braku autoryzacji i niepomyślnym procesie płatności
* 5.A.2 Prezjdź do kroku 1

---

<a id="uc2"></a>
### UC2: Zgłoszenie potwierdzenia wysłania produktu kupującemu

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#br1)

**Scenariusz główny:**
1. [Sprzedający](#ac1) zgłasza do systemu chęć potwierdzenia wysłania produktu kupującemu.
2. System prosi o wgranie dokumnetu potwierdzającego wysłanie produktu.
3. [Sprzedający](#ac1) wgrywa dokument potwierdzający wysłanie produktu.
4. System weryfikuje poprawność formatu dokumentu.
5. System informuje o pomyślnym potwierdzeniu wysłania produktu
6. System informuje [kupującego](#br1) o wysłaniu produktu przez [sprzedającego](#ac1).

**Scenariusze alternatywne:** 

3.A. Wgrano niedozwolony format dokumentu.
* 3.A.1. System informuje o błędnym formacie dokumentu.
* 3.A.2. Przejdź do kroku 2.

---

## Obiewkty biznesowe (inaczje obiekty dziedzinowe lub informatycjne)

### BO1: Aukcja

Aukcja jest formą zawierania transakcji kupna-sprzedaży, w której Sprzedający określa cenę wywoławczą produktu, natomiast Kupujący mogą oferować własną ofertę zakupu każdorazowo proponując kwotę wyższą od aktualnie oferowanej kwoty. Aukcja kończy się po upływie określonego czasu. Jeśli złożona została co najmniej jedna oferta zakupy produkt nabywa ten Kupujący, który zaproponował najwyższą kwotę. 

### BO2: Produkt

Fizyczny lub cyfrowy obiekt, który ma zostać sprzedany w ramach aukcji.

## Reguły biznesowe

<a id="br1"></a>
### BR1: Złożenie oferty

Złożenie oferty wymaga zaproponowania kwoty wyższej niż aktualnie oferowana o minimum 1,00 PLN.


<a id="br2"></a>
### BR2: Rozstrzygnięcie aukcji

Aukcję wygrywa ten z [Kupujący](#ac2)ch, który w momencie jej zakończenia (upłynięcia czasu) złożył najwyższą ofertę.

## Macierz CRUDL


| Przypadek użycia                                  | Aukcja | Produkt | Oferta |
| ------------------------------------------------- | ------ | ------- | --- |
| UC1: Wystawienia produktu na aukcję               | C  |    C    | C |
| UC2: Przekazanie produktu kupującemu                                          |  D  |  ---    | U |
| BR1: zgłoszenie oferty wyższej od wszystkich innych               |    ---   |    ---    | C,U |
| BR2: Przekazanie należności sprzedającemu               |    ---- |    U    | U |
