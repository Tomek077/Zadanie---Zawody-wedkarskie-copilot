# Lekcja: Tworzenie Portalu Zawodów Wędkarskich z Visual Studio Code i GitHub Copilot

## Wprowadzenie

W tej lekcji krok po kroku przejdziemy przez proces tworzenia aplikacji internetowej portalu zawodów wędkarskich, korzystając z Visual Studio Code oraz najnowszej wersji GitHub Copilot. Skupimy się na nauce pisania precyzyjnych promptów, które pomogą nam w efektywnym korzystaniu z Copilota i zrozumieniu wygenerowanych przez niego odpowiedzi.

## Cele lekcji

- Nauka pisania precyzyjnych promptów dla GitHub Copilot.
- Wykorzystanie Copilota do tworzenia kodu HTML, CSS, PHP i zapytań SQL.
- Zrozumienie, jak korzystać z Copilota do edycji plików bezpośrednio w Visual Studio Code.
- Realizacja zadania egzaminacyjnego krok po kroku.

---

## Krok 1: Przygotowanie Środowiska

### 1.1. Instalacja XAMPP

- **Pobierz i zainstaluj XAMPP** z oficjalnej strony: [apachefriends.org](https://www.apachefriends.org/index.html).
- **Uruchom XAMPP Control Panel** i **włącz usługi Apache i MySQL**.

### 1.2. Instalacja Visual Studio Code

- **Pobierz i zainstaluj Visual Studio Code**: [code.visualstudio.com](https://code.visualstudio.com/).

### 1.3. Instalacja GitHub Copilot

- **Zainstaluj rozszerzenie GitHub Copilot** w Visual Studio Code.
- **Zaloguj się** na swoje konto GitHub i **aktywuj Copilota**.

---

## Krok 2: Rozpakowanie Archiwum i Przygotowanie Plików

### 2.1. Rozpakowanie Archiwum

- Na pulpicie znajduje się archiwum `pliki3.zip` zabezpieczone hasłem `ZaWodY7%`.
- **Rozpakuj archiwum**, podając hasło.

### 2.2. Utworzenie Folderu Egzaminacyjnego

- Na pulpicie utwórz folder o nazwie **Twojego numeru PESEL**.
- **Przenieś rozpakowane pliki** do tego folderu.

---

## Krok 3: Operacje na Bazie Danych z phpMyAdmin i Copilot

### 3.1. Tworzenie Bazy Danych `wedkarstwo`

- **Uruchom phpMyAdmin** poprzez przeglądarkę pod adresem `http://localhost/phpmyadmin/`.
- Wykorzystaj Copilota do napisania zapytania SQL tworzącego bazę danych.

#### Prompt dla Copilota:

```sql
-- Napisz zapytanie SQL tworzące bazę danych o nazwie 'wedkarstwo'.
```

#### Oczekiwany wynik:

```sql
CREATE DATABASE wedkarstwo;
```

- **Wykonaj zapytanie** w phpMyAdmin.

### 3.2. Import Tabel z Pliku `baza.sql`

- W phpMyAdmin wybierz bazę danych `wedkarstwo`.
- Przejdź do zakładki **Import** i **zaimportuj plik** `baza.sql`.

### 3.3. Wykonanie Zrzutu Ekranu

- Po imporcie wykonaj **zrzut ekranu** całego ekranu z widocznym paskiem zadań.
- **Zapisz zrzut** jako `import.png` w folderze egzaminacyjnym.

---

## Krok 4: Tworzenie i Wykonywanie Kwerend SQL z Copilotem

### 4.1. Kwerenda 1: Wstawianie Rekordu

#### Prompt dla Copilota:

```sql
-- Wstaw rekord do tabeli 'zawody_wedkarskie' z wartościami:
-- Karty_wedkarskie_id = 2, Lowisko_id = 4, data_zawodow = '2021-09-28', sedzia = 'Andrzej Nowak'.
-- Klucz główny nadawany automatycznie.
```

#### Oczekiwany wynik:

```sql
INSERT INTO zawody_wedkarskie (Karty_wedkarskie_id, Lowisko_id, data_zawodow, sedzia)
VALUES (2, 4, '2021-09-28', 'Andrzej Nowak');
```

- **Wykonaj zapytanie** w phpMyAdmin.
- **Wykonaj zrzut ekranu** i zapisz jako `kw1.jpg`.

### 4.2. Kwerenda 2: Wybieranie Danych

#### Prompt dla Copilota:

```sql
-- Wybierz pola 'id' oraz 'data_zawodow' z tabeli 'zawody_wedkarskie' dla sedziego 'Krzysztof Dobrowolski'.
```

#### Oczekiwany wynik:

```sql
SELECT id, data_zawodow
FROM zawody_wedkarskie
WHERE sedzia = 'Krzysztof Dobrowolski';
```

- **Wykonaj zapytanie** i **zapisz zrzut ekranu** jako `kw2.jpg`.

### 4.3. Kwerenda 3: Wybieranie Danych z Relacją

#### Prompt dla Copilota:

```sql
-- Wybierz 'imie', 'nazwisko', 'punkty' z tabeli 'karty_wedkarskie' dla zwycięzcy zawodów o id 4.
-- Użyj odpowiednich relacji między tabelami.
```

#### Oczekiwany wynik:

```sql
SELECT k.imie, k.nazwisko, k.punkty
FROM karty_wedkarskie k
JOIN zawody_wedkarskie z ON k.id = z.Karty_wedkarskie_id
WHERE z.id = 4;
```

- **Wykonaj zapytanie** i **zapisz zrzut ekranu** jako `kw3.jpg`.

### 4.4. Kwerenda 4: Aktualizacja Danych

#### Prompt dla Copilota:

```sql
-- Zwiększ wartość pola 'punkty' o 2 w tabeli 'karty_wedkarskie' dla rekordu o id 1.
```

#### Oczekiwany wynik:

```sql
UPDATE karty_wedkarskie
SET punkty = punkty + 2
WHERE id = 1;
```

- **Wykonaj zapytanie** i **zapisz zrzut ekranu** jako `kw4.jpg`.

### 4.5. Zapisanie Kwerend

- **Utwórz plik** `kwerendy.txt` w Visual Studio Code.
- **Skopiuj wszystkie zapytania** do pliku.

---

## Krok 5: Przygotowanie Grafiki z Copilotem

### 5.1. Edycja Obrazu `zawody.jpg`

- Otwórz obraz `zawody.jpg` w programie do edycji grafiki (np. GIMP).
- **Prompt dla Copilota nie jest tutaj stosowany**, ale warto zapamiętać kroki:
  - **Odbij obraz** w poziomie, aby osoba była po prawej stronie.
  - **Przeskaluj obraz** z zachowaniem proporcji tak, aby wysokość wynosiła dokładnie 250 px.
  - **Zapisz obraz** pod tą samą nazwą w folderze egzaminacyjnym.

---

## Krok 6: Tworzenie Strony `zawody.html` z Copilotem

### 6.1. Struktura Dokumentu HTML

#### Prompt dla Copilota:

```html
<!-- Utwórz dokument HTML5 z deklaracją języka polskiego i kodowaniem UTF-8.
Tytuł strony: 'Zawody wędkarskie'.
Połącz zewnętrzny arkusz stylów 'styl3.css'.
-->
```

#### Oczekiwany wynik:

```html
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <title>Zawody wędkarskie</title>
    <link rel="stylesheet" href="styl3.css">
</head>
<body>
    <!-- Treść strony -->
</body>
</html>
```

### 6.2. Podział Strony na Sekcje

#### Prompt dla Copilota:

```html
<!-- Dodaj sekcje zgodnie z obrazem 2:
- Góra: sekcja lewa i prawa.
- Środek: sekcja główna.
- Dół: dwie sekcje stopki.
-->
```

#### Oczekiwany wynik:

```html
<body>
    <section id="lewa"></section>
    <section id="prawa"></section>
    <section id="glowna"></section>
    <section id="stopka1"></section>
    <section id="stopka2"></section>
</body>
```

### 6.3. Wypełnienie Sekcji Treścią

#### Blok Lewy

##### Prompt:

```html
<!-- W sekcji 'lewa' dodaj nagłówek h1 o treści 'Zawody polskich wędkarzy'. -->
```

##### Oczekiwany wynik:

```html
<section id="lewa">
    <h1>Zawody polskich wędkarzy</h1>
</section>
```

#### Blok Prawy

##### Prompt:

```html
<!-- W sekcji 'prawa' dodaj obraz 'zawody.jpg' z tekstem alternatywnym 'wędkowanie'. -->
```

##### Oczekiwany wynik:

```html
<section id="prawa">
    <img src="zawody.jpg" alt="wędkowanie">
</section>
```

#### Blok Główny

##### Prompt:

```html
<!-- W sekcji 'glowna' dodaj:
- Nagłówek h3 'Łowiska'.
- Listę punktowaną z elementami: Zalew Węgrowski, Zbiornik Bukówka, Jeziorko Bartbetowskie, Warta-Obrzycko.
- Nagłówek h3 'Dodaj zawody wędkarskie'.
- Formularz wysyłający dane metodą POST do 'zgloszenie.php' z polami:
  - Pole numeryczne 'Łowisko:'.
  - Pole daty 'Data:'.
  - Pole tekstowe 'Sędzia:'.
  - Przycisk reset 'CZYŚĆ'.
  - Przycisk submit 'DODAJ'.
-->
```

##### Oczekiwany wynik:

```html
<section id="glowna">
    <h3>Łowiska</h3>
    <ul>
        <li>Zalew Węgrowski</li>
        <li>Zbiornik Bukówka</li>
        <li>Jeziorko Bartbetowskie</li>
        <li>Warta-Obrzycko</li>
    </ul>
    <h3>Dodaj zawody wędkarskie</h3>
    <form action="zgloszenie.php" method="post">
        <label>Łowisko: <input type="number" name="lowisko"></label><br>
        <label>Data: <input type="date" name="data"></label><br>
        <label>Sędzia: <input type="text" name="sedzia"></label><br>
        <input type="reset" value="CZYŚĆ">
        <input type="submit" value="DODAJ">
    </form>
</section>
```

#### Stopka 1

##### Prompt:

```html
<!-- W sekcji 'stopka1' dodaj odnośnik do 'kwerendy.txt' o treści 'Pobierz'. -->
```

##### Oczekiwany wynik:

```html
<section id="stopka1">
    <a href="kwerendy.txt">Pobierz</a>
</section>
```

#### Stopka 2

##### Prompt:

```html
<!-- W sekcji 'stopka2' dodaj paragraf 'Stronę przygotował: [Twój numer PESEL]'. -->
```

##### Oczekiwany wynik:

```html
<section id="stopka2">
    <p>Stronę przygotował: 12345678901</p> <!-- Zastąp numerem PESEL -->
</section>
```

---

## Krok 7: Tworzenie Arkusza Stylów `styl3.css` z Copilotem

### 7.1. Domyślne Formatowanie

#### Prompt:

```css
/* Ustaw domyślny krój czcionki na Verdana dla całego dokumentu. */
```

#### Oczekiwany wynik:

```css
* {
    font-family: Verdana;
}
```

### 7.2. Stylowanie Sekcji Lewa i Prawa

#### Prompt:

```css
/* Ustaw wspólne style dla #lewa i #prawa:
- Tło SeaGreen, biały kolor czcionki, interlinia 150px, wysokość 260px, rozmiar czcionki 160%.
*/
```

#### Oczekiwany wynik:

```css
#lewa, #prawa {
    background-color: SeaGreen;
    color: white;
    line-height: 150px;
    height: 260px;
    font-size: 160%;
}
```

#### Dodatkowe Style

##### Prompt:

```css
/* Dla #lewa ustaw szerokość 75%. Dla #prawa ustaw szerokość 25% i wyrównanie tekstu do prawej. */
```

##### Oczekiwany wynik:

```css
#lewa {
    width: 75%;
    float: left;
}
#prawa {
    width: 25%;
    float: left;
    text-align: right;
}
```

### 7.3. Stylowanie Sekcji Głównej

#### Prompt:

```css
/* Dla #glowna ustaw tło MintCream i marginesy wewnętrzne 80px. */
```

#### Oczekiwany wynik:

```css
#glowna {
    background-color: MintCream;
    padding: 80px;
    clear: both;
}
```

### 7.4. Stylowanie Stopek

#### Prompt:

```css
/* Dla #stopka1 i #stopka2 ustaw:
- Tło SeaGreen, biały kolor czcionki, szerokość 50%, wysokość 70px, wyrównanie tekstu do środka.
*/
```

#### Oczekiwany wynik:

```css
#stopka1, #stopka2 {
    background-color: SeaGreen;
    color: white;
    width: 50%;
    height: 70px;
    text-align: center;
    float: left;
}
```

### 7.5. Dodatkowe Style dla Kontrolek, Obrazu i Odnośnika

#### Kontrolki (Przyciski i Pola Edycyjne)

##### Prompt:

```css
/* Ustaw dla input margines dolny 20px. */
```

##### Oczekiwany wynik:

```css
input {
    margin-bottom: 20px;
}
```

#### Obraz

##### Prompt:

```css
/* Dodaj do img cień o przesunięciu 15px, rozmyciu 10px i kolorze DimGray. */
```

##### Oczekiwany wynik:

```css
img {
    box-shadow: 15px 15px 10px DimGray;
}
```

#### Odnośnik

##### Prompt:

```css
/* Dla a usuń podkreślenie, ustaw tło MintCream, kolor czcionki SeaGreen, marginesy wewnętrzne 15px, interlinia 70px. */
```

##### Oczekiwany wynik:

```css
a {
    text-decoration: none;
    background-color: MintCream;
    color: SeaGreen;
    padding: 15px;
    line-height: 70px;
}
```

---

## Krok 8: Tworzenie Skryptu `zgloszenie.php` z Copilotem

### 8.1. Połączenie z Bazą Danych

#### Prompt:

```php
<?php
// Połącz się z bazą danych 'wedkarstwo' na localhost, użytkownik 'root', bez hasła.
```

#### Oczekiwany wynik:

```php
$conn = mysqli_connect('localhost', 'root', '', 'wedkarstwo');
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}
```

### 8.2. Pobieranie Danych z Formularza

#### Prompt:

```php
// Pobierz dane z formularza: 'lowisko', 'data', 'sedzia'.
```

#### Oczekiwany wynik:

```php
$lowisko = $_POST['lowisko'];
$data = $_POST['data'];
$sedzia = $_POST['sedzia'];
```

### 8.3. Wstawianie Rekordu do Bazy Danych

#### Prompt:

```php
// Wstaw rekord do tabeli 'zawody_wedkarskie' z Karty_wedkarskie_id = 0 i danymi z formularza.
```

#### Oczekiwany wynik:

```php
$sql = "INSERT INTO zawody_wedkarskie (Karty_wedkarskie_id, Lowisko_id, data_zawodow, sedzia)
VALUES (0, $lowisko, '$data', '$sedzia')";
```

### 8.4. Wykonanie Zapytania i Zamknięcie Połączenia

#### Prompt:

```php
// Wykonaj zapytanie i zamknij połączenie.
```

#### Oczekiwany wynik:

```php
if (mysqli_query($conn, $sql)) {
    echo "Nowy rekord został dodany.";
} else {
    echo "Błąd: " . $sql . "<br>" . mysqli_error($conn);
}
mysqli_close($conn);
?>
```

### 8.5. Pełny Kod `zgloszenie.php`

Po połączeniu wszystkich fragmentów kodu otrzymujemy:

```php
<?php
$conn = mysqli_connect('localhost', 'root', '', 'wedkarstwo');
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$lowisko = $_POST['lowisko'];
$data = $_POST['data'];
$sedzia = $_POST['sedzia'];

$sql = "INSERT INTO zawody_wedkarskie (Karty_wedkarskie_id, Lowisko_id, data_zawodow, sedzia)
VALUES (0, $lowisko, '$data', '$sedzia')";

if (mysqli_query($conn, $sql)) {
    echo "Nowy rekord został dodany.";
} else {
    echo "Błąd: " . $sql . "<br>" . mysqli_error($conn);
}
mysqli_close($conn);
?>
```

---

## Krok 9: Weryfikacja Działania Witryny

- **Przenieś pliki** `zawody.html`, `styl3.css`, `zgloszenie.php` i zmodyfikowany obraz `zawody.jpg` do folderu `htdocs` w XAMPP.
- **Uruchom przeglądarkę** i wpisz adres `http://localhost/zawody.html`.
- **Przetestuj formularz**, wprowadzając przykładowe dane i sprawdź, czy dane są dodawane do bazy.

---

## Krok 10: Zapisanie Nazwy Przeglądarki

- **Utwórz plik** `przeglądarka.txt`.
- **Zapisz w nim nazwę przeglądarki**, której użyłeś (np. "Google Chrome").
- **Umieść plik** w folderze egzaminacyjnym.

---

## Podsumowanie

Gratulacje! Udało Ci się stworzyć pełną aplikację internetową portalu zawodów wędkarskich, korzystając z Visual Studio Code i GitHub Copilot. Nauczyłeś się pisać precyzyjne prompty, które pomagają w efektywnym korzystaniu z Copilota, oraz zrozumiałeś, jak interpretować i modyfikować wygenerowane przez niego odpowiedzi.

---

## Dodatkowe Ćwiczenia

- Spróbuj zmodyfikować styl strony, dodając własne elementy CSS.
- Napisz dodatkowe kwerendy SQL, które wyświetlą inne interesujące dane z bazy.
- Eksperymentuj z różnymi promptami dla Copilota, aby zobaczyć, jak wpływają na generowany kod.

---

## Pytania do Dyskusji

1. Jakie są zalety korzystania z asystentów kodu takich jak GitHub Copilot?
2. W jaki sposób precyzyjne prompty wpływają na efektywność pracy z Copilotem?
3. Jak można poprawić bezpieczeństwo aplikacji internetowej tworzonej w PHP?

---
