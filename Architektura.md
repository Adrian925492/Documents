# Architektura #

## Paradygmaty programowania ##

**Programowanie strukturalne** - paradygmat zakłada podział programu na procedury i hierarchicznie ułożone bloki, z wykorzystaniem struktur kontrolnych w postaci instrukcji wyboru i pętli. Paradygmat wyklucza istnienie skoków, zakłąda zasadę 1 wyjścia ze struktur. Opiera się na założeniu, że każdy kod można rekursywnie dzielić na mniejsze procedury, aż będzie można go zapisać z użyciem struktur warunkowych i pętli. Podstawowe struktury warunkowe to: *sekwencja - wykonywanie ciągu kolejnych instrukcji, instrukcje warunkowe if i switch*. Paradygmat odrzuca stosowanie skoków (goto) lub przerwań pętli (break).

**Programowanie obiektowe** - Paradygmat, w którym programy definiuje się za pomocą obiektów - elementów łączących dane i zachowania (metody). Program obiektowy reprezentowany jest jako zbiór takich obiektów i interakcji między nimi. Programowanie obiektowe ułątwia pisanie, konserwację i ponowne używanie fragmentów kodu. Cechami programowania obiektowego są: polimorfizm, hermetyzacja, dziedziczenie. 

**Programowanie funkcyjne** - Paradygmat zakłąda, że podstawową jednostką programu jest funkcja. Programowanie funkcyjne odrzuca zmienne. Nacisk kłądzie się na wartościowanie funkcji.

____

## Definicje ##

**Odwracanie zależności** - Metoda polega na zastąpieniu bezpośredniej zależności między konkretnymi klasami zależnością odwrotną. Jedna z klas w tym schemacie odwołuje się (zależy) od interfejsu drugirj klasy, z któej ta dziedziczy. Dzięki temu obie klasy zależą od interfejsu. W praktyce następuje odwrócenie zależności od klasy zależnej do interfejsu poprzez relację dziedziczenia.

**Miękkość oprgramowania** - zdolność oprogramowania do poddawania się zmianom. Mówimy, że oprogramowanie jest miękkie, gdy łątwo jest wprowadzić zmiany w module.

**Mikroserwisy** - zbiór małych usług, za pomocą których komponenty komunikują się ze sobą. Zbiór mikroserwisów pozwala na spełnienie reguł biznesowych. Każdy mikroserwis jest traktowany jak małą, oddzielna aplikacja.

**Poziom oprogramowania** - definiujemy jako odległość danej procedury od warstwy wejścia - wyjścia danego programu. Im bliżej - tym niższy poziom oprogramowania. 

**Wtyczka** - dodatkowy moduł oprogramowania rozszerzający funkcjinalność podstawowego modułu. Wtyczki komunikują się z modułem podstawowym za pomocą API.

**Reguły biznesowe** - Zbiór reguł określających funkcjonalności danego systemu, będące jego podstawą biznesową, czyli takie, które są źródłem zysku (np. dodawanie produktów do koszyka w sklepie internetowym). Są krytyczne z punktu widzenia architektury i muszą być implementowane.

**Istotne dane biznesowe** - Dane, na których pracują reguły biznesowe w celu spełnienia oczekiwanych funkcjonalności.

**Encje** - Obiekty zawierające reguły(ę) biznesowe i istotne dane biznesowe, a także implementujące je. Encja jest implementacją reguł biznesowych.

**Przypadki użycia** - Opisują sposoby użycia danego systemu bez względu na punkt widzenia reguł biznasowych. Przypadki użycia są koncepcją niższego poziomu niż encje, bo odnoszą się do konkretnego ssytemu, a encje odnoszą się do abstrakcji. 

**Zasada zależności** - Zależności w kodzie źródłowym powinny zawsze wskazywać w kierunku wyższej warstwy. Jeśli tak nie jest - powinniśmy stosować odwracanie zależności.

**Komponenty traktowane jako niskopoziomowe**
1) Komponent main
2) Testy
3) Frameworki
4) Bazy danych

**Problem kruchych testów** - pojawia się, gdy testy zbyt zależą od aplikacji, a zmiana w aplikacji implikuje zmianę w testach.

**Prawo demeter** - mówi, że komponent lub klasa powinna zależeć wyłącznie od swoich sąsiadów. W praktyce oznacza to, że metody klas nie powinny wywoływać metod innych klas bezpośrednio - mogą za to robić to przez interfejsy.

**Zasada DRY** - Don't repeat yourself - Oznacza, że powinniśmy unikać w kodzie duplikatów, gdyż każdy duplikat zwiąksza ryzyko pomyłki przy ewentualnej zmianie (możemy zmienić jeden z wersji i zapomnieć zmienić drugi).

**Zasada YAGNI** - You aren't gonna need it - Mówi o tym, że jeśli jakaś funkcjinalność nie jest potrzebna (nie jest na dany moment wymagana), to nie powinna być implementowana "na zapas", ponieważ takie działanie spowodowałoby dodaniem wielu funkcjonalności, które zwiększą skomplikwoanie kodu, a co więcej, część z nich w finalnym systemie nigdy nie będzie użyta.

**Firmware** - część oprogramowania bezpośrednio powiązana z hardware

**Software** - część oprogramowania pracująca niezależnie od sprzętu. Firmware i software pozinny być oddzielone granicą architektoniczną.

**Bare metal** - Część oprogramownai abezpośrednio osadzona na sprzęcie (bez użycia OSa). Oprogramowanie bare metal pozostaje w bezpośredniej interakcji z warstwą sprzętową.

**DDD** - Domain driven design - Podejście używane w rozwoju oprogramowania, polegające na koncentrowaniu się na zadanej dziedzinie i logice z zadanej dziedziny. W DDD celem jest pisanie oprograowania będącego odzwierciedleniem rzeczywistego systemu. W DDD odwzorowujemy zagadnienia z dziedziny biznesowej na kod.

**HAL** – warstwowa abstrakcji sprzętu, istnieje na potrzeby obsługi sprzętu działającego pod nią.

**PAL** – procesor abstraction layer – warstwa abstrakcji procesora, zawiera np. obsługę przerwań. Jest opcjonalna.

**OSAL** – operating system abstraction layer – warstwa oddielająca OS od aplikacji. Jeśli używamy Osa należy go potraktować jak szczegół.

____

## Zasady SOLID ##

**SRP** - Klasa powinna mieć tylko jeden powó do zmian (powinna odpowiedać przed jednym aktorem) Powinniśmy tak dzielić system na klasy, aby gdy zajdzie potrzeba zmiany, dotyczyła ona tylko jednej klasy. Zasada wprowadza porządek w kodzie.

**OCP** - Klasy powinny być otwarte na rozszerzenia, ale zmaknięte na zmiany. Jeśli chcemy, możemy więc rozszerzyć zachowanie klasy w podklasach, ale powinniśmy unikać modyfikowania istniejących klas. Dodanie funkcjonalności powinno odbywać się poprzez rozszerzenie istniejącej w podklasie. Zasada jest spełniona,jeśli zmiany w kkasach niższych warstw nie implikują zmian w klasach wyższych warstw. Aby to myło możliwe, zależnosci między komponentami powinny być jednostronne - od niższych, do wyższych warstw.

**LSP** - Funkcje, któe używają wskaźnikó lub referencji do klas bazowych, muszą być również w stanie używać obiektów podklas tych klas bazowych w ten sam sposób. Oznacza to, że nie możemy zmieniać funkcjonalności metod w podklasach (przeciążać), możemy je tylko rozszerzać, tak, aby dąło się wymiennie stosować nadklase i podklasy. Gdyby tak nie było, to klienty musiałyby rozróżniać, czy pracują na nadklasie czy podklasie, inaczej podklasy, z powodu innej implementacji, mogłyby być użyte w niewłaściwy sposób.

**ISP** - Zasada segregacji interfejsów. Jeżeli kilka kals korzysta z danej klasy, i wszystkie korzystają z różnych części tego samego interfejsu, to powinniśmy podzielić interfejs na kilka mniejszych tak, aby klasy nie otrzymywały tych części interfejsu, których nie potrzebują.

**DIP** - Zasada odwracania zależności. Wszystkie ależnosci w kodzie powinny odnosic się do abstrakcji. W praktyce jest to niemożliwe, ale wystarczy, że tak jest na granicach zbiorów klas. Efekt uzyskujemy stosując odwracanie zależności.

Stabilna architektura:

>	Nie odnosi się do konkretnych, przez to ulotnych klas

>	Nie dziedziczy po konkretnych klasach

>	Nie pokrywa konkretnych metod (Liskov)

>	Nie powołuje się na konkretne obiekty

___

## Zasady tworzenia komponentów ##

**REP** - Podstawą ponownego użycia komponentu jest jego nr wydania. Komponenwy powinny być więc niezalezie wersjonowane, a informacje o zmianach w kolejnych wersjach powinny być jawne.

**CCP** - W ramach jednego komponentu powinny znaleźć się klasy, któe mogą się zmienić z tego samego powodu. Zasada jest przeniesieniem zasady SRP na poziom komponentów.

**CRP** - W ramach jednego komponentu powinny znaleźć się klay, które zazwyczaj współpracują ze sobą, aby nie implikować konieczości użycia kilku komponentów do spełnienia danej funkcjonalności.

W praktyce architektura powinna być kompromisem między tymi trzema zasadami. 
___

## Zasady łączenia komponentó ##

**Zasada zależnoći niecyklicznych** - Należy unikać łączenia komponentów w taki sposób, aby tworzy zamknięte grafy zależności. Tego rodzaju cykle są niebezpieczne, ponieważ zmiana w którymkolwiek węźle cyklu implikuje zmiany w każdym pozostałym. Należy rozdzielać strukturę zależonosćci tak, aby komponenty niższej warstwy zależały od komponentów wyższej warstwy. Do łamania cykli należy używać odwracania zależności.

**Zasada stabilnych zależności** – zależności w kodzie powinny być kierowane w stronę elementu stabilnego. Oznacza to, że żelazności powinniśmy zawsze kierować w stronę komponentu, który będzie miał małe prawdopodobieństwo zmian. Żaden komponent uznany za stabilny nie powinien zależeć od komponentu uznanego za niestabilny, bo wtedy zmiana w niestabilnym komponencie pociąga za sobą zmianę w stabilnym. Najbardziej stabilnymi komponentami są abstrakcje. Miara stabilności opisuje stosunek zależności wychodzących do wszystkich zależności. Im więcej jest zależności wychodzących, tym komponent jest niej stabilny. Im więcej zależności przychodzących, a mniej wychodzących, tym komponent stabilniejszy. Nie da się rezygnować z niestabilnych komponentów, bo uniemożliwiłoby to modyfikowanie kodu.

**Zasada stabilnych abstrakcji** – komponent powinien być tak abstrakcyjny, jak jest stabilny. Oznacza to, że komponent uznany za stabilny powinien być również abstrakcyjny, aby jego abstrakcja uniemożliwiała jego zmianę. Niestabilne komponenty powinny być konkretnymi implementacjami, a stabilne – abstrakcjami. Miarą abstrakcji jest stosunek liczby klas abstrakcyjnych w komponencie do liczby wszystkich klas, jakie posiada komponent.

___

## Poziomy rozdzielenia komponentów ##

**Poziom kodu źródłowego** – możemy definiować zależności między poziomami kodu źródłowego tak, aby zmiany w jednych modułach nie implikowały zmian w innych modułach. W tym trybie wszystkie komponenty korzystają z tej samej przestrzeni adresowej i komunikują się ze sobą za pomocą wywołań funkcji. 

**Poziom instalacji** – Komponenty tworzą odrębnie instalowalne jednostki, np. prekompilowane biblioteki lub biblioteki dynamicznie dołączalne. Zmiany w jednym module nie wymuszają (z zasady) zmian w innych, ale komunikowanie się tych modułów bywa bardziej kosztowne. Komponenty mogą, ale nie muszą korzystać z tej samej p-ni adresowej i komunikować się za pomocą wywołań funkcji, ale mogą być też rozdzielone na różne procesy lub wątki.

**Poziom usług** – zapewnia największą izolacje, ale jest też najbardziej kosztowny we współdziałaniu komponentów. Komponenty komunikują się ze sobą za pomocą mikroserwisów. Każda jednostka jest zupełnie niezależna od innych, komunikuje się poprzez zdefiniowany interfejs. 

___

## Granice architektoniczne ###

**Granica architektoniczna** - rodzielenie elementów systemu tak, aby te nie wpływały na siebie nawzajem. Granice należy prowadzić między komponentami ważnymi, a tymi niej ważnymi, np. GUI - logika. Przekraczanie granic polega na wywołąniu metod z jednej strony granicy przez element z drugiej.

Metody przekraczania granic:

1)	Bezpośrednie wywołanie funkcji – najprostsza z metod, ale dająca najmniejszą izolację i będąca jednocześnie najmniej kosztowna. Metoda działa we wszystkich rodzajach rozdzielenia.

2)	Metody dostępowe między procesami lokalnymi – polega na wywołaniu metod dostępowych do komunikacji między procesami. Metoda działa tylko na poziomie rozdzielenia instalacji i usług.

3)	Wysyłanie spójnych żądań – metoda działa tylko na poziomie usług, jest najbardziej kosztowna i zapewnia największą izolację.

Z powodu kosztów należy, jeśli to możliwe, unikać metod 2 i 3.

**Granice częściowe** – niepełne granice, tworzone tam, gdzie z powodów zasobowych niepożądane jest tworzenie pełnych granic architektonicznych. Granice częściowe można rozbudować do pełnych granic, jeśli zajdzie potrzeba.

Metody tworzenia granic częściowych:

1)	Przygotowanie komponentów do utworzenia pełnej granicy, ale pozostawienie ich bez implementacji tej granicy. Oznacza, że musimy przygotować odpowiednie interfejsy do rozdzieleni komponentów, ale nie rozdzielamy go. Nakład pracy jest taki sam, ale nie trzeba utrzymywać dwóch komponentów.

2)	Granica jednowymiarowa – polega na tym, że zamiast dwóch interfejsów, tworzymy jeden. Komunikacja jest jednostronna, nakład pracy jest o połowę mniejszy, ale i stopień izolacji jest mniejszy. W razie potrzeby można rozbudować taką granicę do pełnowymiarowej.

3)	Fasada – najprostszy rodzaj granicy, polega na skorzystaniu ze wzorca fasada. Zapewnia izolację przy przekraczaniu granicy, ale nie zapewnia odwrócenia zależności, bo wszystkie komponenty zależne od fasady są również zależne od komponentów, które korzystają z fasady.
