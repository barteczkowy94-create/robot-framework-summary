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

## Tydzien 4 - Quiz (sobota, 2026-08-15) - Dni 16-18


1. Co jest glownym celem wzorca Page Object w projektach Robot Framework?
   a) Przyspieszenie uruchamiania testow  b) Oddzielenie locatorow/logiki
      strony od kroków testowych, zeby zmiana UI wymagala edycji w jednym
      miejscu  c) Generowanie raportow  d) Zastapienie plikow Resource

2. Jaka jest zalecana konwencja nazewnictwa test case'ow w Robot Framework?
   a) camelCase jak w Javie  b) Czytelne zdania opisujace zachowanie, np.
      "Zaloguj uzytkownika z poprawnymi danymi"  c) Same skroty (TC001,
      TC002)  d) Nazwy plikow zamiast nazw testow

3. Do czego sluzy plik `Jenkinsfile`/workflow GitHub Actions w kontekscie
   Robot Framework?
   a) Do przechowywania danych testowych  b) Do automatycznego uruchamiania
      testow (np. przy kazdym pushu) oraz publikowania raportow (log.html,
      report.html) jako artefaktow builda  c) Do formatowania kodu  d) Do
      definiowania keywordow

4. Jak najlepiej opublikowac `log.html`/`report.html` z pipeline'u CI/CD?
   a) Wkleic ich tresc do logow konsoli builda  b) Zapisac jako artefakty
      builda (np. `archiveArtifacts`/`upload-artifact`), zeby byly dostepne
      do pobrania po zakonczeniu builda  c) Nie ma potrzeby ich zachowywac
      d) Wyslac emailem do calego zespolu za kazdym razem

5. Do czego sluzy Robotidy?
   a) Do generowania raportow HTML  b) Do automatycznego, deterministycznego
      formatowania kodu .robot/.resource (wciecia, spacje, wyrownanie)
      c) Do uruchamiania testow rownolegle  d) Do zarzadzania zmiennymi
      srodowiskowymi

6. Czym rozni sie rflint/robocop od Robotidy?
   a) Niczym, to synonimy tego samego narzedzia  b) rflint/robocop to
      lintery wykrywajace problemy jakosciowe (np. brak [Documentation],
      zbyt dlugie testy), a Robotidy tylko formatuje styl kodu  c) Robotidy
      sluzy do uruchamiania testow, a rflint do ich zapisywania  d) Oba
      sluza wylacznie do generowania dokumentacji

7. Jak najskuteczniej wyizolowac i zdebugowac jeden, zawieszajacy sie test
   bez uruchamiania calego suite'u?
   a) Uzyc flagi `--test "Nazwa testu"` (ewentualnie z `--loglevel DEBUG`)
   b) Usunac wszystkie inne testy z pliku  c) Zakomentowac cala reszte
      kodu recznie za kazdym razem  d) Nie da sie tego zrobic selektywnie

8. Dlaczego struktura projektu z podzialem na `tests/`, `resources/` i
   `results/` (lub podobna) ulatwia utrzymanie duzego zestawu testow?
   a) RF tego wymaga, inaczej nie dziala  b) Oddziela kod testowy, wspoldzie-
      lone keywordy/Page Objecty i generowane wyniki, co ulatwia nawigacje
      i unika przypadkowego commitowania wynikow  c) Przyspiesza wykonanie
      testow  d) Nie ma to zadnego znaczenia praktycznego

**Odpowiedzi:** 1-b, 2-b, 3-b, 4-b, 5-b, 6-b, 7-a, 8-b

## Tydzien 4 - Fiszki

- Page Object Pattern -> locatory i akcje na stronie trzymane w dedykowanym
  Resource/keywordach, testy odwoluja sie tylko do nazw keywordow (nie do
  surowych selektorow)
- Nazewnictwo testow -> pelne, czytelne zdania (Title Case) zamiast skrotow
  typu TC001 - nazwa testu = dokumentacja
- CI/CD (Jenkins/GitHub Actions) -> automatyczne uruchamianie `robot` przy
  kazdym pushu/PR + archiwizacja `log.html`/`report.html` jako artefaktow
- `archiveArtifacts` (Jenkins) / `actions/upload-artifact` (GitHub Actions)
  -> publikuja wyniki testow po zakonczeniu builda, nawet gdy testy padly
- Robotidy -> formater kodu (styl, wciecia, spacje) - uruchamiany z flaga
  `--check` w CI wykrywa niesformatowany kod bez modyfikacji plikow
- rflint / robocop -> lintery jakosci (brak dokumentacji/tagow, zduplikowane
  keywordy, zbyt dlugie testy) - traktuj jak eslint/pylint dla RF
- `--test "Nazwa testu"` + `--loglevel DEBUG` -> izolacja i szczegolowe
  debugowanie pojedynczego testu bez uruchamiania calego suite'u
- Struktura projektu (`tests/`, `resources/`, `results/`) -> rozdziela kod
  testow, wspoldzielone keywordy/Page Objecty i generowane wyniki (te
  ostatnie zwykle w `.gitignore`)

================================================================================

## Tydzien 5 - Quiz (piatek, 2026-08-21) - Dni 19-23

1. Do czego sluzy pole `Metadata` w sekcji `*** Settings ***`?
   a) Definiuje zmienne globalne  b) Dodaje dodatkowe informacje (autor,
      wersja) widoczne w `report.html`  c) Importuje biblioteke  d) Ustawia
      tagi dla wszystkich testow

2. Czym sa prefiksy `Given`/`When`/`Then` przy nazwach keywordow w stylu BDD?
   a) Osobnymi slowami kluczowymi wymagajacymi rejestracji  b) Czysto
      kosmetyczna konwencja - RF pomija je przy dopasowywaniu nazwy
      keywordu  c) Dzialaja wylacznie w plikach Resource  d) Wymagaja
      dedykowanej biblioteki BDD

3. Ktory keyword BuiltIn zastepuje reczna petle z `Sleep` czekajaca na
   spelnienie warunku (np. gotowosc zasobu)?
   a) `Repeat Keyword`  b) `Wait Until Keyword Succeeds`  c) `Run Keyword If`
   d) `Sleep Until True`

4. Czym rozni sie `Skip` od `Pass Execution`?
   a) Niczym, to synonimy  b) `Skip` oznacza test jako SKIP, `Pass
      Execution` wymusza PASS mimo niewykonania reszty kroku  c) `Skip`
      dziala tylko w `*** Tasks ***`  d) `Pass Execution` zatrzymuje caly
      suite

5. Jakie slowo kluczowe w RF 7.0+ zastepuje `Set Test/Suite/Global
   Variable`?
   a) `Set Variable If`  b) `VAR` z argumentem `scope=`  c) `Evaluate`
   d) `Create Variable`

6. Jaki jest domyslny zasieg zmiennej ustawionej przez `VAR` bez podania
   `scope=`?
   a) GLOBAL  b) SUITE  c) LOCAL  d) TEST

7. W ktorym pliku definiuje sie `Suite Setup`/`Suite Teardown` wspolny dla
   calego katalogu testow (nie pojedynczego pliku)?
   a) `conftest.robot`  b) `__init__.robot`  c) `common.resource`
   d) `suite.yaml`

8. Gdzie dostepne sa zmienne `${TEST_STATUS}` i `${TEST_MESSAGE}`?
   a) W kazdym kroku kazdego testu  b) Tylko w `Test Teardown`  c) Tylko w
      `Suite Setup`  d) Tylko w plikach Resource

9. Co zwraca `Get From Dictionary` z parametrem `default`, gdy podany klucz
   nie istnieje w slowniku?
   a) Zawsze rzuca blad  b) Zawsze zwraca `None`  c) Zwraca podana wartosc
      domyslna zamiast rzucac blad  d) Usuwa caly slownik

10. Jak zachowuje sie `Sort List` wzgledem oryginalnej listy?
    a) Zwraca nowa, posortowana liste, nie zmieniajac oryginalu  b) Sortuje
       liste w miejscu (in-place) i zwraca `None`  c) Dziala wylacznie na
       listach liczb  d) Wymaga biblioteki `String`

**Odpowiedzi:** 1-b, 2-b, 3-b, 4-b, 5-b, 6-c, 7-b, 8-b, 9-c, 10-b

## Tydzien 5 - Fiszki

- `Metadata` (Settings) -> dodatkowe informacje (autor, wersja) widoczne w
  `report.html`, niezalezne od `[Tags]`
- `Given`/`When`/`Then`/`And`/`But` -> tylko konwencja nazewnicza, RF
  ignoruje te prefiksy przy dopasowywaniu keywordu
- `Wait Until Keyword Succeeds` (np. `5x    1s`) -> dynamiczny retry z
  limitem czasu zamiast sztywnego `Sleep`
- `Skip`/`Skip If` vs `Pass Execution` -> `Skip` = wynik SKIP w raporcie,
  `Pass Execution` = wymuszony PASS mimo niewykonania reszty kroku
- `VAR    ${x}    wartosc    scope=LOCAL|TEST|SUITE|GLOBAL` (RF 7.0+) ->
  nowoczesny zamiennik `Set Test/Suite/Global Variable`, domyslnie LOCAL
- `${{ python_expr }}` -> wyrazenie Python wprost w miejscu uzycia zmiennej
  (dla prostych obliczen), `Get Variable Value` -> bezpieczny odczyt z
  wartoscia domyslna
- `__init__.robot` -> `Suite Setup`/`Suite Teardown` dla calego katalogu
  (nie moze zawierac `*** Test Cases ***`)
- `${TEST_STATUS}` / `${TEST_MESSAGE}` -> dostepne wylacznie w `Test
  Teardown`, pokazuja wynik i komunikat bledu dopiero co zakonczonego testu
- `Get From Dictionary    ...    default=` -> bezpieczny odczyt klucza bez
  ryzyka bledu przy jego braku
- `Sort List` -> in-place, zwraca `None`; `Get Slice From List` -> nowa
  lista-fragment bez modyfikacji oryginalu

================================================================================
