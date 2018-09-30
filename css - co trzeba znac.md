


<!-- todo - przenieść do drugiego pliku  -->
## Najważniejsze kwestie dotyczące CSS, które należy poznać
W tym rozdziale, opisuję filary CSS. Musisz je poznać, aby wydajnie pracować z kaskadowymi arkuszami stylów oraz zrozumieć problemy, które pojawiają się podczas tworzenia stron WWW. 
Specificity
* http://www.standardista.com/wp-content/uploads/2012/01/specificity3.pdf
* https://codepen.io/KamilNaja/pen/gXqjqb
Specyficzność to reguły, które określają style CSS, brane pod uwagę podczas stylowania danego elementu. Elementy o wyższej specyficzności, nadpisują elementy o niższej specyficzności.
W skrócie - im więcej gwiazdek, tym większa speficzność. 
important **********
styl inline *****
id ***
class **
tag *
Pseudoelementy i pseudoklasy nie zmieniają specyficzności. 


Elementu id nie nadpisuje się wieloma elementami o określonej klasie - jego speficzność jest wyższa o rząd jednostek. Podobnie jest z innymi elementami.
Element stylowany za pomocą dwóch klas, jest bardziej specyficzny od tego, który ma jedną klasę. 
Uwaga - jeśli musimy stosować bardzo specyficzne selektory CSS, oznacza to często błąd w strukturze stylów. 
!important zwiększa specyficzność w taki sposób, że żaden inny styl nie może go nadpisać (chyba, że posiada także deklarację !important i ma większą specyficzność). 
Box sizing
* Defaultowo w przeglądarce stosowany jest box-sizing: content-box. Oznacza, że marginesy oraz paddingi i bordery diva, nie są dodawane do jego wymiarów
* Border-box - najczęściej używany - gdy ustawiamy konkretne with lub height, element będzie miał dokładnie taki wymiar
Defaultowo w bootstrapie mamy ustawiony box-sizing: border-box, dzięki czemu, elementy zachowują się przewidywalnie. Szerokość 100px = zawsze 100px
Przykłady 
* https://codepen.io/KamilNaja/pen/JOxBze

Wiedza na temat box-sizing jest niezbędna między innymi wtedy, gdy chcemy umiejscowić na stronie dwa elementy jeden obok drugiego. Jeśli mają ustawioną szerokość 50% i dodatkowe paddingi, to jeśli box-sizing ustawiony jest na content-box, elementy nie zmieszczą się obok siebie i błąd będzie trudny do zdiagnozowania.

## Normalize CSS, reset CSS
Resetowanie domyślnych stylów przeglądarki, lub ustawienie je na takie same wartości. Zwykle jest domyślnie dostępne we frameworku CSS, takim, jak Bootstrap.
Częstszą praktyką jest stosowanie normalize.css, ponieważ umożliwia uzyskanie lepszego wyglądu strony, bez konieczności dodawania dużej ilości stylów.
W niektórych przypadkach, można zdecydować się na samodzielne wyzerowanie tych wartości CSS, które nam przeszkadzają podczas pracy.

h1, h2, h3, h4, h5, h6 {
        margin-top: 0;
}

## Poznaj moc selektorów 
CSS posiada wiele selektorów, które pozwalają na stylowanie mniej standardowych elementów lub wybieranie ich, na podstawie specyficznych zasad. 
Przykłady - http://pierwszycommit.blogspot.com/2017/07/kilka-przydatnych-znacznikow-css-ktore.html
https://code.tutsplus.com/pl/tutorials/the-30-css-selectors-you-must-memorize--net-16048


Selektory w CSS, są prawie takie same, jak te używane w jQuery
Warto poznać bardziej zaawansowane selektory CSS, ponieważ znacznie ułatwiają one wybieranie niestandardowych elementów.


Elementy blokowe i inlinowe
Elementy blokowe zajmują całą dostępną szerokość elementu, w którym się znajdują. Gdy ustawimy obok siebie 2 elementy blokowe, zawsze będą jeden pod drugim (chyba, że zmienimy to ustawienie). Przykłady - nagłówki <hx>, divy, <p>. Element blokowy może zawierać w sobie inne elementy blokowe lub inlinowe.


Elementy inlinowe zajmują jedynie tyle miejsca, ile potrzebują i “zawijają się”. Przykładem elementu inline (liniowego), jest span. Elementy tego typu, nie powinny zawierać elementów blokowych!
Przykłady
https://codepen.io/KamilNaja/pen/POVBMZ


Elementy blokowe mają 100% szerokości, o ile, nie ustawimy jej na inną wartość.
Sposób wyświetlania elementu można zmienić za pomocą CSS.
 
Jak rozmieścić na stronie różne elementy?
Deweloperzy, którzy dopiero zaczynają przygodę z HTML i CSS, często zastanawiają się, jakich tagów html użyć na stronie, do różnych elementów.


Aby odpowiedzieć sobie na to pytanie, zapoznaj się z opisem najważniejszych tagów HTML, ze szczególnym uwzględnieniem ich semantyki. 
Semantyka na stronie HTML wskazuje na to, jaką rolę odgrywa dany element na stronie. Jest to bardzo ważne, gdy strona jest przetwarzana przez takie narzędzia, jak na przykład przeglądarki tekstowe, czytniki ebooków czy programy odczytujące treść strony osobom niewidomym i słabowidzącym.
<div> to element bez znaczenia sematycznego, który oznacza wydzieloną część strony. Lepszym wyborem może być zastosowanie tagu 

```css 
<header>
```
 lub 
 ```css 
 <footer>
 ```
 jeśli dana część strony oznacza jej nagłówek lub stopkę. 
<main> może być znacznikiem, w którym umieścimy główną treść strony, natomiast <aside>, wskaże przeglądarce lub innemu urządzeniu na to, że dana informacja jest dodatkowo, poza główną treścią strony. 
Osobne paragrafy tekstu umieszcza się w znacznikach <p>, natomiast tekst dodatkowo wyróżniający się, można ująć w znaczniki <span> i nadać mu inne stylowanie. 


Podczas tworzenia stron, stosuje się różne konwencję. Do tworzenia układu strony nie należy używać tabel. Menu na stronie, jest zawsze listą nienumerowaną. Listy na stronie, należy ująć w odpowiedni znacznik listy.


Dobrym źródłem informacji na temat znaczenia semantycznego poszczególnych elementów HTML, jest Mozilla Developer Network (MDN). Informacje na stronie W3Schools, często są nieprawidłowe lub przeterminowane
## Tworzenie linii między elementami
## Pseudoelementy
## Before i after
Te pseudoselektory, pozwalają na tworzenie prostych elementów, które mają pojawiać się na stronie przed lub po danym elemencie. Można w nich umieścić także tekst. Wykorzystuje się je przede wszystkim do dodawania ozdobników. Elementy before i after muszą mieć ustawioną wartość content (może być pusta) i domyślnie ustawiają się inlinowo. 
Ich jeszcze jedną zaletą, jest możliwość dodania jakiegoś elementu na stronie, bez dodawania kodu HTML.
Przykład - chcę, by każdy nagłówek h1 był ozdobiony gwiazdką

```css
h1:after {
        content: “*”,
}
```

Pseudoelementy pozwalają na tworzenie zaawansowanych kształtów, bez dodawania niepotrzebnego kodu HTML do strony.


## Pseudoklasy
Pseudoklasy pozwalają na jeszcze lepsze wybieranie elementów HTML do stylowania, bez konieczności dodawania do kodu nowych klas. 
Poniżej kilka często używanych pseudoklas:
.element:first-child 
.element:nth-child(2)
.element:last-child


##Wyśrodkowanie elementu w poziomie
Elementu blokowego nie można wyśrodkować, jeśli nie ma ustawionej szerokości (zajmuje domyślnie cały obszar. Jeśli ma nadaną szerokość, to wyśrodkujemy go, przez 
.centered{ 
    margin-left: auto;
    margin-right: auto;
    max-width: 500px;
} 

Przykłady
 https://codepen.io/KamilNaja/pen/POVBMZ

## Wyśrodkowanie elementu inline w poziomie
text-align: center
Przykłady - https://codepen.io/KamilNaja/pen/POVdoN


## Wyśrodkowanie elementu w pionie
Element inline o długości mniej, niż jedna linia - można mu nadać padding góra-dół, lub zastosować odpowiedni line-height (taka sama wartość, jak wysokość elementu)
Przykład - https://codepen.io/KamilNaja/pen/QOYVoB


Jeśli element inline zawiera kilka linijek, należy użyć flex.


Wyśrodkowanie elementu za pomocą position: absolute
```css
.centered {
   position: absolute;
   transform: translate(-50%, -50%);
   left: 50%;
   top: 50%;
}  
```

Przykład - https://codepen.io/KamilNaja/pen/QOYVoB przykład 2


Źródła - https://css-tricks.com/centering-css-complete-guide/


## Wyśrodkowanie elementu za pomocą Flex
display: flex pozwala na bardzo wygodne wyśrodkowywanie elementów. 
https://codepen.io/KamilNaja/pen/QOYVoB?editors=1100 - przykład 3

## Jak przesunąć element?
Najlepiej unikać przesuwania o x pixeli, ponieważ może to spowodować nieoczekiwane błędy. Dobrym rozwiązaniem jest zastosowanie paddingu dla elementu nadrzędnego.
Przykład - 
https://codepen.io/KamilNaja/pen/jadvEL - btn1


Gdy nadamy elementowi position: relative lub absolute, możemy go przesuwać względem pierwotnego położenia (relative), lub względem okna przeglądarki albo elementu nadrzędnego, który ma zadeklarowaną pozycję inną niż static (absolute). Unikamy używania position absolute; Przykład - jw, btn3


Gdy element nie ma pozycji abs lub rel, możemy go przesunąć za pomocą wartości margin. Przykład - jw, btn4


Po przesunięciu elementu, należy sprawdzić, czy nie nachodzi on na inne elementy przy innych szerokościach ekranu!
Najlepszym rozwiązaniem jest takie ustawienie elementów w HTML, by zachodziło jak najmniej konieczności zmian ich ustawienia za pomocą przesuwania.


## Float
Float służy (służył), do tworzenia odpowiedniego layoutu strony, przez ustawienie opływania elementów. Dzięki niemu, elementy blokowe mogą ustawiać się obok siebie.


Przykład - https://codepen.io/KamilNaja/pen/aVXaNX
Uwaga - gdy element nie chce “zejść” poniżej, należy sprawdzić, czy w elemencie nadrzędnym, mamy wystarczająco dużo miejsca i czy stosujemy dobry box-model. Nowe sposoby określania wyświetlania elementów (flex oraz grid), pozwalają na znacznie łatwiejsze rozmieszczanie elementów na stronie. 


Elementy floatowane układają się obok siebie, jednak zwykle chcemy w którymś miejscu strony powrócić, do standardowego ustawiania elementów blokowych jeden pod drugim. W takiej sytuacji, musimy wyczyścić opływanie elementów przez 
clear: both.
Kolejne elementy HTML, będą ustawiane znów w standardowy sposób. 

## Float - pułapka 
Elementy floatowane nie nadają wysokości elementowi nadrzędnemu!!!
Trzeba stosować haki
https://codepen.io/KamilNaja/pen/dZaqOb


## RWD caveats!
Nadawanie szerokości i wysokości jest słabe!
Gdy nadajesz elementowi szerokość ustaloną w pikselach, prawie na pewno będzie ona niewłaściwa, po zmianie szerokości strony, na przykład, podczas przeglądania na innym urządzeniu. Lepszym rozwiązaniem, jest ustalenie szerokości procentowo. Możesz też wykorzystać własność calc()
```css
div {
        width: calc(90% - 20px)
}
```

Jeśli chcesz ograniczyć długość diva, warto mu nadać max-width - nie wpływa na szerokość strony, a jedynie, na maksymalną szerokość elementu.


Gdy nadasz divowi wysokość, przy większej ilości treści, treść zacznie z niego “wychodzić”. 
https://codepen.io/KamilNaja/pen/bYzxja


Jeśli chcesz, żeby strona miała konkretną szerokość na przykład na dużym ekranie, skorzystaj z media queries.
Zdjęcia na stronie RWD
Prawie zawsze dodajemy do zdjęcia max-width: 100%. W Bootstrapie, mamy do tego klasę img-responsive.
https://codepen.io/KamilNaja/pen/dZaqgG
Ta sama zasada tyczy się elementów Video i iFrame.


Narzędzia
Inspektor (narzędzia F12)
  

Przeglądarka Google Chrome posiada szereg opcji, które ułatwiają wizualne tworzenie stron WWW. 


Edytor wizualny cieni

Do strony możemy nawet dodać własny arkusz CSS i edytować go lokalnie na dysku, a następnie wkleić do naszego IDE.


SASS
Preprocesor CSS, pozwalający na stosowanie łatwiejszej i krótszej składni, podczas stylowania strony.
http://sass-lang.com/. Kompiluje się go do zwykłego CSS.
Do jego działania, wymagany jest Ruby. Polecane narzędzia - Compass.

```css
.wrapper2 {
  width: 200px;
  .inside {
    transform: translate(-50%, -50%);
    left: 50%;
    top: 50%;
  }
}
kod powyżej, kompiluje się do 
.wrapper2 {
  width: 200px;
}
.wrapper2 .inside {
  transform: translate(-50%, -50%);
  left: 50%;
  top: 50%;
}
```
Perfect Pixel
https://chrome.google.com/webstore/detail/perfectpixel-by-welldonec/dkaagdgjmgdmbnecmcefdhjekcoceebi
Dodatek do przeglądarki, który pozwala na ustawienie elementów idealnie w ten sam sposób, jak w pliku PSD. Moim zdaniem, nie ma to większego sensu, ponieważ projekt graficzny, nigdy nie uwzględni wszystkich szerokości ekranu i sposobu, w jaki ma na nich wyglądać strona. 
Emmet
https://emmet.io/
Pozwala na znacznie szybsze tworzenie kodu HTML i CSS. Oferuje wtyczki dla większości edytorów tekstowych. 
Caniuse 
https://caniuse.com/


Przykład - 
   * Znalazłem na StackOverflow super trick w CSS, który pozwoli rozwiązać mi moje zadanie
   * A czy sprawdzałeś na CANIUSE, czy możemy go użyć w naszym projekcie? Twój trick jest wspierany przez 0.00001 przeglądarek. Lepiej użyć float.
Specyfikacja CSS zmienia się każdego dnia, ponieważ dodawane są do niego nowe opcje. Jeśli chcesz użyć nowej opcji w swoim projekcie, sprawdź, czy będzie ona wspierana przez docelowe przeglądarki. W wielu projektach stosowanie display: flex oraz display: grid, nie będzie dobrym wyborem, ponieważ te technologie nie są jeszcze wspierane przez wszystkie przeglądarki.
### Pix to Pix 

Backstop JS
Świetne narzędzie do tworzenia testów wizualnych strony internetowej. Podczas pisania kodu CSS, może dojść do nieumyślnego nadpisania stylów w innym miejscu i “zepsucia” podstrony. BackstopJS pozwala na stworzenie serii testów wyglądu strony oraz sprawdzenie, czy na stronie zmieniły się tylko te elementy, od których to oczekiwaliśmy.
BackstopJS to także sposób na szybkie przejrzenie wyglądu strony na różnych urządzeniach oraz zapoznawanie się z nowymi treściami, które zostały dodane na stronę. 
https://github.com/garris/BackstopJS


Codepen
Źródła wiedzy


https://developer.mozilla.org
https://css-tricks.com/
http://ferrante.pl/books/html/


# Styles guide CSS