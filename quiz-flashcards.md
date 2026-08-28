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

## Tydzien 5 - Quiz (sobota, 2026-08-22) - Dni 19-23

1. Do czego oprocz Library sluzy sekcja *** Settings ***?
   a) Tylko do importu bibliotek  b) Rowniez do Resource, Variables,
      Metadata oraz Suite/Test Setup/Teardown i Test Tags  c) Tylko do
      zmiennych  d) Tylko do tagowania testow

2. Czym sa "embedded arguments" w Robot Framework?
   a) Argumentami wplecionymi bezposrednio w nazwe slowa kluczowego (np.
      "Zaloguj jako ${rola}")  b) Zmiennymi srodowiskowymi  c) Argumentami
      z linii polecen  d) Argumentami przekazywanymi tylko przez plik .yaml

3. Kiedy warto uzyc Wait Until Keyword Succeeds zamiast Sleep?
   a) Nigdy, Sleep jest zawsze lepszy  b) Gdy chcemy powtarzac wywolanie
      keyworda az do sukcesu lub limitu prob/czasu, zamiast czekac sztywno
      ustalony czas  c) Tylko w testach API  d) Tylko razem z Run Keywords

4. Jaki jest domyslny zasieg (scope) zmiennej ustawionej przez VAR bez
   podania parametru scope=?
   a) GLOBAL  b) SUITE  c) LOCAL  d) TEST

5. Co zwraca Get Variable Value, gdy podana zmienna nie istnieje i NIE
   podano wartosci domyslnej?
   a) Blad wykonania testu, ktory przerywa suite  b) Cicho ${None}  c) Pusty
      string automatycznie konwertowany na 0  d) RF przerywa cale uruchomienie

6. Co definiuje plik __init__.robot umieszczony w katalogu z testami i
   czego NIE moze zawierac?
   a) Definiuje Suite Setup/Teardown dla calego katalogu; nie moze zawierac
      sekcji *** Test Cases ***  b) Definiuje pojedynczy test; moze zawierac
      wszystko  c) Sluzy tylko do importu bibliotek  d) Jest wymagany w
      kazdym katalogu z testami

7. W ktorym miejscu testu dostepne sa zmienne ${TEST_STATUS} i
   ${TEST_MESSAGE}?
   a) W dowolnym miejscu testu, od poczatku  b) Tylko w Test Setup
   c) Wylacznie w Test Teardown / [Teardown] - po zakonczeniu wykonania
      testu  d) Tylko w Suite Setup

8. Co robi Get From Dictionary z parametrem default, gdy podany klucz nie
   istnieje w slowniku?
   a) Rzuca wyjatek  b) Zwraca wartosc domyslna zamiast rzucac blad
   c) Zwraca None niezaleznie od default  d) Usuwa klucz ze slownika

**Odpowiedzi:** 1-b, 2-a, 3-b, 4-c, 5-b, 6-a, 7-c, 8-b

## Tydzien 5 - Fiszki

- *** Settings *** -> obejmuje nie tylko Library, ale tez Resource,
  Variables, Metadata, Suite/Test Setup/Teardown i Test Tags
- Embedded arguments -> argument wpleciony w nazwe keyworda (np. "Zaloguj
  jako ${rola}"), kod czyta sie jak zdanie
- Prefiksy BDD (Given/When/Then/And/But) -> czysto kosmetyczne, RF je
  ignoruje przy dopasowywaniu nazwy keyworda
- Wait Until Keyword Succeeds -> retry z limitem prob/czasu (np. "5x 1s"),
  lepsze niz Sleep przy niestabilnych/asynchronicznych zasobach
- VAR (RF 7.0+) -> jedno slowo kluczowe zamiast Set Test/Suite/Global
  Variable, zasieg przez scope=LOCAL|TEST|SUITE|GLOBAL (domyslnie LOCAL)
- Get Variable Value -> bezpieczny odczyt zmiennej z wartoscia domyslna,
  bez rzucania wyjatku jak przy zwyklym odwolaniu ${zmienna}
- __init__.robot -> definiuje Suite Setup/Teardown dla calego katalogu,
  nie moze zawierac wlasnych *** Test Cases ***
- ${TEST_STATUS} / ${TEST_MESSAGE} -> dostepne wylacznie w Test Teardown/
  [Teardown], nie w Test Setup ani w ciele testu
- Get From Dictionary z default -> unika bledu przy brakujacym kluczu,
  zwraca wartosc domyslna zamiast rzucac wyjatek
- Sort List -> sortuje liste w miejscu (in-place) i zwraca None - nie
  przypisuj wyniku do nowej zmiennej

================================================================================

## Tydzień 6 - Quiz (piątek, 2026-08-28) - Dni 25-29

1. Do czego służy `Wait Until Keyword Succeeds` w kontekście testów API?
   a) Do wymuszenia sztywnego opóźnienia przed żądaniem  b) Do ponawiania
      wywołania keyworda (np. GET On Session) aż do sukcesu lub limitu
      prób/czasu, przydatne przy asynchronicznych endpointach  c) Tylko do
      testów UI  d) Do automatycznego retry na poziomie samej biblioteki
      RequestsLibrary bez potrzeby dodatkowego keyworda

2. Jak ustawić Test Template na poziomie całego suite'u zamiast pojedynczego testu?
   a) Nie da się, Template działa tylko per test  b) Przez `Test Template`
      w sekcji *** Settings ***, wtedy każdy wiersz w *** Test Cases ***
      staje się zestawem argumentów dla wskazanego keyworda  c) Przez
      `[Template]` w każdym teście osobno  d) Przez plik konfiguracyjny YAML

3. Czym różni się `Set Tags` od `[Tags]` w Robot Framework?
   a) Niczym, to synonimy  b) `[Tags]` to statyczna deklaracja w definicji
      testu, `Set Tags` to keyword dodający tagi dynamicznie w trakcie
      wykonania testu  c) `Set Tags` działa tylko na poziomie suite'u
   d) `[Tags]` można używać tylko raz na plik

4. Co oznacza wzorzec z `NOT` przy selektywnym uruchamianiu testów, np.
   `--include smokeNOTslow`?
   a) Uruchamia testy z tagiem smoke, ale wyklucza te, które mają
      jednocześnie tag slow  b) Uruchamia wszystkie testy poza tagiem smoke
   c) Jest niepoprawną składnią  d) Uruchamia testy z tagiem "smokeNOTslow"
      jako dosłowną nazwą

5. Czego NIE może zawierać plik `__init__.robot`?
   a) Sekcji *** Settings ***  b) Suite Setup/Teardown  c) Sekcji
      *** Test Cases ***  d) Importów Resource/Library

6. Do czego służy polecenie `python -m robot.libdoc`?
   a) Uruchamia testy w trybie debug  b) Generuje dokumentację HTML/XML
      keywordów z resource'u lub biblioteki  c) Formatuje kod .robot
      (jak Robotidy)  d) Sprawdza jakość kodu (jak rflint)

7. Jaką korzyść daje dodanie type hints do argumentów metody w
   bibliotece Pythona dla RF (np. `def f(self, a: int)`)?
   a) Żadną, RF ignoruje adnotacje typów  b) RF automatycznie konwertuje
      przekazany argument tekstowy na wskazany typ przed wywołaniem  c)
      Przyspiesza wykonanie testu  d) Wymusza walidację argumentu tylko
      w trybie DEBUG

8. Dlaczego do logowania z poziomu biblioteki Pythona należy używać
   `robot.api.logger` zamiast `print()`?
   a) `print()` jest wolniejszy  b) `print()` trafia do konsoli, a nie do
      log.html, więc informacja ginie w standardowym przebiegu (np. w CI)
   c) `print()` jest przestarzały w Pythonie  d) Nie ma żadnej różnicy

**Odpowiedzi:** 1-b, 2-b, 3-b, 4-a, 5-c, 6-b, 7-b, 8-b

## Tydzień 6 - Fiszki

- Wait Until Keyword Succeeds -> ponawia wywołanie keyworda (np. z
  RequestsLibrary) aż do sukcesu lub limitu prób/czasu, zamiast sztywnego Sleep
- Test Template (poziom suite'u, *** Settings ***) -> każdy wiersz w
  *** Test Cases *** to zestaw argumentów dla jednego wspólnego keyworda
- DataDriver -> biblioteka RF do wczytywania danych testowych z
  zewnętrznego pliku (CSV/XLSX) i generowania z niego osobnych testów
- Set Tags / Remove Tags -> dynamiczne dodawanie/usuwanie tagów w trakcie
  wykonania testu, w odróżnieniu od statycznego [Tags] w definicji
- Keyword Tags (@keyword(tags=[...])) -> tagi nadane keywordowi w kodzie
  Pythona, dziedziczone automatycznie przez testy, które go używają
- Wzorzec NOT w --include/--exclude -> np. "smokeNOTslow" uruchamia testy z
  tagiem smoke, wykluczając te, które mają też tag slow
- __init__.robot -> definiuje Suite Setup/Teardown dla całego katalogu,
  nie może zawierać własnej sekcji *** Test Cases ***
- python -m robot.libdoc -> generuje dokumentację HTML/XML keywordów z
  resource'u lub biblioteki na podstawie [Documentation] i docstringów
- Type hints w argumentach metody Pythona -> RF automatycznie konwertuje
  przekazany string na wskazany typ (int, float, bool) przed wywołaniem
- robot.api.logger zamiast print() -> jedyny poprawny sposób logowania z
  poziomu biblioteki Pythona, żeby wpis trafił do log.html
