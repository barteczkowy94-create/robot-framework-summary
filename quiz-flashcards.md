# Quiz i Fiszki - Robot Framework

## Tydzien 1 - Quiz (piatek, 2026-07-24) - Podstawy skladni RF

1. Ile minimalnie spacji musi rozdzielac argumenty w pliku .robot?
   a) 1  b) 2  c) 4  d) Tabulacja jest zabroniona

2. Jak poprawnie nazywa sie sekcja z przypadkami testowymi?
   a) *** Tests ***  b) *** Test Case ***  c) *** Test Cases ***  d) *** TestCases ***

3. Do czego sluzy "..." na poczatku linii w RF?
   a) Komentarz  b) Kontynuacja poprzedniej linii  c) Import biblioteki  d) Nic nie robi

4. Ktory znak rozpoczyna komentarz w Robot Framework?
   a) //  b) #  c) --  d) ;

5. Co sie stanie, jesli argumenty rozdzielimy tylko jedna spacja?
   a) Blad skladni  b) RF zlepi je w jeden argument  c) Zadziala normalnie  d) Test zostanie pominiety

**Odpowiedzi:** 1-b, 2-c, 3-b, 4-b, 5-b

## Tydzien 1 - Fiszki

- Sekcje pliku .robot -> *** Settings ***, *** Variables ***, *** Test Cases ***, *** Keywords ***
- Separator argumentow -> min. 2 spacje lub tabulacja
- Kontynuacja linii -> ...
- Komentarz -> #
- [Documentation] -> opis testu/keywordu, widoczny w log.html i report.html
- [Tags] -> etykiety do selektywnego uruchamiania testow (--include, --exclude)

================================================================================

## Dzien 7 - Quiz (czwartek, 2026-07-30) - RequestsLibrary do testow API

1. Ktorego keywordu nalezy uzyc, aby wykonac zadanie GET w ramach wczesniej utworzonej sesji?
   a) Get Request  b) GET On Session  c) Send GET  d) Open Session

2. Do czego sluzy parametr `expected_status` w keywordach `*_On Session`?
   a) Ustawia timeout zadania  b) Automatycznie weryfikuje kod odpowiedzi HTTP  c) Okresla format wysylanych danych  d) Nic nie robi, jest tylko dokumentacja

3. Jak poprawnie odczytac dane JSON z obiektu `response` zwroconego przez RequestsLibrary?
   a) `${response.data}`  b) `${response.json()}`  c) `${response.body}`  d) `Get Json    ${response}`

4. Ktora biblioteka jest zwykle uzywana razem z RequestsLibrary do walidacji struktury odpowiedzi JSON (np. slownikow)?
   a) String  b) OperatingSystem  c) Collections  d) DateTime

5. Gdzie nalezy przechowywac tokeny API i dane logowania uzywane w testach?
   a) Bezposrednio w pliku .robot jako literal  b) W zmiennych srodowiskowych lub bezpiecznym pliku konfiguracyjnym  c) W komentarzu przy tescie  d) W nazwie test case'u

**Odpowiedzi:** 1-b, 2-b, 3-b, 4-c, 5-b

## Dzien 7 - Fiszki

- `Create Session` -> tworzy sesje HTTP z nazwa i adresem bazowym (base URL), uzywana pozniej w keywordach `*_On Session`
- `GET/POST/PUT/DELETE On Session` -> wykonuja zadania HTTP w ramach istniejacej sesji, zamiast starszych `Get Request`/`Post Request`
- `expected_status` -> parametr keywordu weryfikujacy kod odpowiedzi HTTP, zglasza czytelny blad przy niezgodnosci zamiast recznego sprawdzania
- `${response.json()}` -> dostep do body odpowiedzi jako danych Pythona (dict/list); `${response.status_code}` -> kod HTTP
- `Dictionary Should Contain Key` (Collections) -> walidacja obecnosci klucza w odpowiedzi JSON przed odczytem wartosci
- Tokeny/API keys -> zawsze w zmiennych srodowiskowych/pliku konfiguracyjnym (`%{API_TOKEN}`), nigdy jako literal w pliku .robot

================================================================================

## Tydzien 2 - Quiz (piatek, 2026-07-31) - Dni 2-8

1. Ktory keyword z biblioteki BuiltIn sluzy do warunkowego przerwania testu
   z wlasnym komunikatem?
   a) Should Be True  b) Run Keyword If  c) Fatal Error  d) Log To Console

2. Jaki jest zasieg zmiennej ustawionej przez `Set Global Variable`?
   a) Tylko biezacy Test Case  b) Tylko biezacy plik .robot
   c) Caly przebieg wykonania (wszystkie suity)  d) Tylko biezacy Keyword

3. W ktorej sekcji definiuje sie kod uruchamiany raz przed wszystkimi
   testami w danym pliku .robot?
   a) [Setup] w Test Case  b) Test Setup  c) Suite Setup  d) Task Setup

4. Ktora biblioteka standardowa udostepnia keyword `Get Length` do
   sprawdzania dlugosci listy lub stringa?
   a) String  b) Collections  c) OperatingSystem  d) DateTime

5. Czym rozni sie SeleniumLibrary od nowszej Browser Library (Playwright)?
   a) Niczym, to ta sama biblioteka  b) Browser Library dziala tylko na Linux
   c) Browser Library oparta jest o Playwright i oferuje m.in. lepsza
      obsluge oczekiwan i wielu przegladarek jednoczesnie  d) SeleniumLibrary
      nie wspiera lokalizatorow CSS

6. Ktory keyword RequestsLibrary tworzy trwala sesje HTTP do wielu zadan?
   a) GET On Session  b) Create Session  c) Create Dictionary  d) Get Request

7. Do czego sluzy `expected_status` w keywordach RequestsLibrary typu
   `GET On Session`?
   a) Ustawia timeout zadania  b) Okresla oczekiwany kod HTTP odpowiedzi i
      powoduje blad testu, jesli sie nie zgadza  c) Wybiera metode HTTP
   d) Zwraca body odpowiedzi jako string

8. Co robi `[Template]` w Test Case w Robot Framework?
   a) Ustawia szablon dokumentacji  b) Kazdy wiersz danych pod nazwa testu
      traktuje jako osobne wywolanie wskazanego Keywordu  c) Importuje
      biblioteke zewnetrzna  d) Generuje raport HTML

**Odpowiedzi:** 1-c, 2-c, 3-c, 4-b, 5-c, 6-b, 7-b, 8-b

## Tydzien 2 - Fiszki

- Fatal Error -> natychmiast przerywa cala egzekucje suite'a (BuiltIn)
- Set Global Variable -> zmienna widoczna we wszystkich suitach do konca
  wykonania
- Suite Setup / Suite Teardown -> kod uruchamiany raz przed/po wszystkich
  testach w pliku/katalogu
- Get Length -> keyword Collections/BuiltIn zwracajacy dlugosc listy,
  slownika lub stringa
- Browser Library (Playwright) -> nowoczesna alternatywa dla SeleniumLibrary,
  szybsza, z natywnym auto-waitingiem
- Create Session -> RequestsLibrary, tworzy nazwana sesje HTTP z bazowym URL
- expected_status -> parametr walidujacy kod odpowiedzi HTTP wprost w
  keywordzie zadania
- [Template] -> mechanizm Data-Driven Testing; kazdy wiersz danych = osobny
  przypadek w raporcie

================================================================================

## Tydzien 3 - Quiz (sobota, 2026-08-08) - Dni 9-15

1. Ktora flaga CLI uruchamia testy oznaczone konkretnym tagiem?
   a) `--tagname`  b) `--include`  c) `--select`  d) `--filter`

2. Do czego sluza pliki Resource (`.resource`/`.robot` z `Resource`)?
   a) Do przechowywania wynikow testow  b) Do wspoldzielenia keywordow i
      zmiennych miedzy wieloma suitami  c) Do konfiguracji CI/CD  d) Tylko
      do przechowywania danych testowych

3. Jak Robot Framework rozpoznaje wlasny keyword w bibliotece Pythonowej
   zaimportowanej przez `Library`?
   a) Musi dziedziczyc po klasie `RobotLibrary`  b) Wystarczy publiczna
      metoda/funkcja w klasie lub module `.py`  c) Musi miec rozszerzenie
      `.rflib`  d) Musi byc napisana w Javie

4. Ktory plik generowany po uruchomieniu testow zawiera szczegolowy,
   krok-po-kroku zapis wykonania (przydatny do debugowania)?
   a) `output.xml`  b) `report.html`  c) `log.html`  d) `summary.txt`

5. Ktory keyword sprawdza, ze dany keyword rzuca OKRESLONY, oczekiwany blad?
   a) `Run Keyword And Ignore Error`  b) `Run Keyword And Expect Error`
   c) `Fail`  d) `Should Be Equal`

6. Skad NALEZY pobierac sekrety (hasla, tokeny API) uzywane w testach?
   a) Z literalow w pliku `.robot`  b) Ze zmiennych srodowiskowych/sejfu
      sekretow, nigdy z kodu commitowanego do repo  c) Z komentarzy w
      kodzie  d) Z nazwy test case'u

7. Jaka sekcja pliku `.robot` sluzy do definiowania procesow RPA zamiast
   testow?
   a) `*** Test Cases ***`  b) `*** Tasks ***`  c) `*** Processes ***`
   d) `*** Robots ***`

8. Dlaczego w procesie RPA warto obudowac ryzykowny krok blokiem
   TRY/EXCEPT zamiast pozwolic, by caly przebieg zakonczyl sie bledem?
   a) Bo TRY/EXCEPT jest szybszy obliczeniowo  b) Aby pojedynczy blad (np.
      jeden zly rekord) nie przerywal calego, dzialajacego bez nadzoru
      procesu  c) Bo `Fail` nie istnieje w trybie RPA  d) Nie ma to
      znaczenia, oba podejscia sa rownowazne

**Odpowiedzi:** 1-b, 2-b, 3-b, 4-c, 5-b, 6-b, 7-b, 8-b

## Tydzien 3 - Fiszki

- `--include`/`--exclude` -> selektywne uruchamianie testow po tagach
  (`[Tags]`) bez modyfikacji kodu testow
- Resource file -> plik `.resource`/`.robot` importowany przez `Resource`,
  wspoldzieli keywordy/zmienne miedzy suitami (modularizacja)
- Custom Keyword w Pythonie -> zwykla klasa/funkcje w pliku `.py`
  zaimportowane przez `Library`, kazda publiczna metoda staje sie keywordem
- `log.html` -> szczegolowy log krok-po-kroku (debugowanie); `report.html`
  -> podsumowanie wynikow; `output.xml` -> surowe dane maszynowe
- `Run Keyword And Expect Error` -> weryfikuje TRESC oczekiwanego bledu;
  `Run Keyword And Ignore Error` -> tylko ignoruje blad bez weryfikacji
- TRY/EXCEPT/ELSE/FINALLY (RF 5+) -> nowoczesna obsluga wyjatkow z
  dostepem do tresci bledu przez `AS ${zmienna}`
- Zmienne srodowiskowe (`%{ZMIENNA}`) i `--variablefile` -> oddzielaja
  sekrety/dane srodowiskowe (dev/staging/prod) od kodu testow
- `*** Tasks ***` -> sekcja RPA (zamiast `*** Test Cases ***`); nie mozna
  mieszac obu typow sekcji w jednym pliku
- rpaframework (`RPA.Excel.Files`, `RPA.Tables`, `RPA.HTTP` itd.) ->
  gotowe biblioteki do automatyzacji procesow biznesowych (RPA)

================================================================================

