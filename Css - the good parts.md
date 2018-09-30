# CSS - the good, bad and ugly parts

## Zamiast wstępu

CSS pozwala na nadawanie stronie internetowej lub aplikacji odpowiedniego wyglądu. W przeciwieństwie do języków programowania, takich, jak na przykład JavaScript lub C#, praca z CSS wydaje się bardzo łatwa i niewymagająca zbyt dużej ilości wiedzy, do osiągnięcia ciekawych efektów. 

Niestety, ale wraz z rozwojem Twojej strony, CSS zaczyna sprawiać coraz więcej problemów. 

Okazuje się, że dobre poznanie CSS, wymaga nie tylko praktyki i stosowania szybkich rozwiązań ze StackOverflow, ale także, zrozumienia, jak arkusze stylów działają. 

Gdy poznasz te zasady, będziesz mógł zapobiegać wielu problemom ze stylowaniem jeszcze zanim się pojawią.

Kaskadowe arkusze stylów, są łatwe do nauczenia się, ale bardzo trudne jest osiągnięcie w nich dużej biegłosci. 

Ten artykuł powstał podczas zmagania się z poprawianiem kodu CSS, pisanego przez osoby nie mające pojęcia o stylowaniu elementów. 

Kamil Naja
Praga
2017 - 2018

# Złe praktyki w CSS

CSS pozwala na określanie wyglądu poszczególnych elementów na stronie. Niestety, ale gdy Twoja strona się rozrasta i ilość kodu CSS rośnie, praca staje się coraz trudniejsza. Kod staje się nieprzewidywalny, a dodawanie kolejnych funkcjonalności, wymaga ciągłego przeszukiwania arkusza. 

Poprawki zajmują coraz więcej czasu. 

Ten poradnik, pozwoli Ci się uchronić przed problemami, które wychodzą dopiero wtedy, gdy Twój projekt staje się coraz bardziej rozbudowany.

## Nadpisywanie stylów frameworka!
Gdy nadpiszesz domyślny styl, framework przestanie zachowywać się tak, jak chciał to autor. Prowadzi to do problemów, przy rozwoju aplikacji lub strony internetowej. Ty i Twoi koledzy z zespołu, przestają mieć pewność, jakich klas css mogą używać. 

Aby wprowadzić modyfikację, dodaj dodatkową klasę - modyfikator.

```css
.container {
        width: 500px !important; // cała reszta strony psuje się
}
```

Aby zmniejszyć szerokość strony, dodaj osobną klasę.

```css
.container-smaller {
        width: 500px; // nadal paskudnie, ale trochę lepiej
}
```

### Używanie important
Kod nadziany !importantami jak dobra kasza skwarkami, jest zwykle pisany przez osoby, które nie rozumieją zasad kaskadowości stylów CSS. Jeśli nie musisz, nie używaj znacznika important!.
Przed zastosowaniem !important, sprawdź specyficzność danego elementu i pomyśl, jak ją nadpisać. 
Używając important, działasz krótkowzrocznie i nadajesz elementowi styl, który będzie bardzo trudno zmienić. W przyszłości, gdy kod CSS się zmieni, sprawi to problemy.
Important jest wykorzystywany przez twórców pluginów czy szablonów CSS, chcących mieć pewność, że ich styl zostanie nadany. 


#### Jak działa important? 
Important zwiększa specyficzność w taki sposób, że nie można nadpisać elementu w inny sposób, jak tylko przez używanie jeszcze bardziej specyficznego stylu (także zawierającego !important). 

Jeśli musisz nadpisywać style z użyciem !important, pomyśl o przekształceniu kodu w taki sposób, by uniknąć stosowania tej deklaracji. 
https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity


### Stylowanie po tagach lub Id elementu, zamiast po jego klasie
Struktura HTML strony może się zmienić, dlatego lepiej jest używać reużywalnych klas. Jako programiści front-end, często zapominamy o tym, że style CSS mogą być wykorzystywane także w aplikacjach, które nie wykorzystują tagów HTML. Przykładem jest React Native.


Elementy semantyczne (np <main>, <article>, <header>, <Hx>) na stronie HTML, mają odzwierciedlać przeznaczenie danego elementu, a nie jego wygląd. Niektóre dobrze przemyślane frameworki, usuwają domyślne stylowanie z elementów, a następnie, pozwalają na dodanie własnych stylów jedynie za pomocą klas. Na tym pomyśle opiera się między innymi Bulma.css.

Element z danym Id może znajdować się na stronie tylko raz, a jeśli znajduje się na stronie więcej razy, może powodować to nieoczekiwane działanie na przykład JS.
 
Tworząc stronę internetową, staraj się komponować ją z reużywalnych elementów, które będzie można wykorzystać na wielu podstronach. Wyklucza to używanie stylowania za pomocą id. 
Przykład - chcesz, aby input na stronie oznaczony określonym id, miał większy margines od innych inputów. Pomyśl jednak, czy nie lepiej jest zastosować osobnej klasy i w przyszłości, wykorzystać ją do tworzenia elementów o podobnym stylowaniu.

Przykład
```css
header {
        font-size: 50px;
}
```

```css
.header { /* stylujemy po klasie, nie po tagu */
        font-size: 50px
}
```

### Stylowanie inline - bardzo trudno jest je potem nadpisać
Stylowanie inline może przybierać dwie, bardzo kłopotliwe formy. 
Po pierwsze, style inline są nadawane przez kod Javascriptu. 
Drugim sposobem jest wpisanie ich “na sztywno” w element, w celu jego wystylowania. Jedna i druga metoda, powoduje problemy z późniejszym utrzymaniem kodu. 


Style inline są stosowane dlatego, że dają natychmiastowe efekty i oszczędzają nam wysiłku umysłowego, przy wybieraniu elementów CSS za pomocą selektorów. Niestety, ale z czasem, musisz coraz dłużej zastanawiać się nad tym, jak nadpisać takie style.


Jeszcze jedną wadą stylów inline jest to, że nie pozwalają one na wielokrotne wykorzystywanie kodu.
Stylowanie przypominające inlinowe można “osiągnąć” także za pomocą klas CSS, co również należy do złych praktyk.
Framework CSS Bootstrap, umożliwia stosowanie takich klas, jak :

* float-left
* pull-left
* mt-10

Metodologia Atomic CSS zaleca stosowanie takich klas, jak
* mt-10 /* margin-top: 10px */
* pt-10 /* padding-top: 10px */

W praktyce, wykorzystanie takiego kodu, nie różni się niczym od stylowania inlinowego i należy go unikać!

### Stylowanie za pomocą JS
### Stosowanie za mało ogólnych selektorów, gdy można skorzystać z ich ogólniejszej wersji
Kod początkujących deweloperów często zyskuje na jakości, po usunięciu wielu wartości niepotrzebnie wpisanych w bardzo szczegółowo określone elementy. Praktyka podpowiada, że zanim napiszemy zbyt szczegółowy selektor CSS, powinniśmy przejrzeć inne elementy strony i prawdopodobnie, skorzystać z wartości już zdefiniowanych w kodzie.
Przykłady
Na stronie znajduje się menu i każdy jego element li ma nadane inne stylowanie, na przykład za pomocą osobnej klasy lub właściwości nth-child. 
```css
<ul>
        <li class=”menu-item-1”>
                Lorem
        </li>
        <li class=”menu-item-2”>
                Ipsum<
        /li>
        <li class=”menu-item-3”>
                Dolor
        </li>
<ul>
```


Bardzo prawdopodobne jest to, że programista w takiej sytuacji mógłby wykorzystać jedną (a nie trzy) klasę CSS, ponieważ poszczególne elementy menu, zwykle wyglądają tak samo. 


Na całej stronie używana jest czcionka Arial. Powinna ona zostać nadana całościowo dla strony, a nie, dla każdego elementu z osobna. 
```css
/* nu nu nu, nie robimy tak */

h1 {
        font-family: Arial
}


h2 {
        font-family: Arial
}
```
Podobna zasada dotyczy większości selektorów CSS używanych na stronie, takich, jak font-size, line-height. Powinieneś dążyć do tworzenia kodu, który można wykorzystać także w innych miejscach aplikacji.

### Używanie magicznych liczb

Przed nadaniem elementowi określonej wysokości lub szerokości, pomyśl, czy w przyszłości się on nie zmieni. Praktyka pokazuje, że ustawienie jakiejś wartości na sztywno, niemal zawsze powoduje kolejne problemy w przyszłości.

Przykład:

W szablonie PSD, dostajesz element, który ma 500 na 500 pixeli i zajmuje mniej więcej pół szerokości ekranu. Jeśli nadasz mu takie wymiary, po dodaniu większej ilości treści, element “rozwali się”. Z kolei, ustawienie na sztywno szerokości, powoduje kolejny problem - przy zmniejszeniu okna przeglądarki, elementy przestają się mieścić. 

Znacznie lepszym rozwiązaniem, jest nadanie elementowi szerokości 50% na dużym ekranie i ustawienie breakpointu za pomocą media queries, by na wąskim ekranie, zajmował on na przykład 100% szerokości. 


Inny przykład

Element znajduje się na środku ekranu. Aby go tam umieścić, developer używa
```css
.element {
        margin-left: 743px;
}
```
Kolejny przykład

```css
@media (min-width: 1200px)
    .silly-selector {
        width: 1680px;
    }
```

```css
.dostep_toggle {
    width: 35%; /* !!! */
}
```
Wartości ustawione za pomocą wartości bezwzględnych także mogą się przydać podczas tworzenia strony. Element opisany na przykładzie, może mieć z każdej strony padding 15 pikseli, który będzie dobrze wyglądał zarówno na małym, jak i na dużym ekranie. 


Dużo więcej na ten temat dowiesz się z książki Ethana Marcotte “Responsive Web Design”. 

### Wymyślanie koła na nowo, czyli stosowanie własnych rozwiązań, gdy mamy już gotowe we frameworku lub istniejącym kodzie.

Przykład - tworzenie własnego okna modalnego na stronie, która używa już Bootstrapa. Stosowanie gotowych rozwiązań pozwala na szybszą pracę oraz wyeliminowanie nieoczekiwanych błędów, które pojawiają się podczas tworzenia kodu od nowa. 


Z czasem, poznasz coraz więcej bibliotek, które rozwiązują popularne problemy front-endowe na różnych poziomach trudności. Jeśli znajdziesz na cudzej stronie jakąś interesującą funkcję, możesz podejrzeć jej kod lub sprawdzić, jaka jest nazwa pluginu czy biblioteki, która ją obsługuje. Nie wpadnij jednak w nawyk, dodawania do prostych stron kilku różnych bibliotek ważących po kilkanaście kilobajtów, które obsługują tylko jeden ficzer.


Jeśli używasz dużych bibliotek, takich, jak na przykład Bootstrap, powinieneś dobrze poznać jego możliwości. Być może okaże się, że do wykonania kolejnej funkcjonalności, nie musisz dodawać jeszcze jednej biblioteki, ponieważ jej obsługa, już jest wbudowana. 


Wymyślanie koła na nowo, dotyczy także niewielkich zadań, z którymi zmagamy się w codziennej pracy. Powracając do przykładu Bootstrapa - posiada on wbudowane klasy, rozwiązujące takie problemy, jak:
* Wyśrodkowywanie elementów
* Zmniejszanie elementów takich, jak <img>, by mieściły się na wszystkich rozdzielczościach ekranu.
* Usuwanie różnic w wyświetlaniu różnych elementów pod wieloma przeglądarkami
* Zachowanie konsekwentnego stylowania strony we wszystkich miejscach. 
Umiejętnie wykorzystując te klasy, możesz skupić się na ważniejszych zadaniach, niż ciągłe zastanawianie się, dlaczego Twój kod CSS nie działa. Znacznie przyśpiesza to tworzenie strony WWW. 

Wymyślanie koła na nowo, często zamienia się w "wymyślanie na nowo kwadratowego koła". Tworząc własne elementy, napotykamy na wiele problemów i tworzymy ich obejścia, przez co powstaje "kwadratowe koło". Aby tego uniknąć, warto zapoznać się przynajmniej z dokumentacją frameworka CSS, z którego korzystamy. 
```css
.wrong_selector {
    padding: 20px 35px 20px 35px; /* - skąd te wartości??? */
}
```

<!-- todo - opisać nadpisywanie domyślnych wartości, które nic nie daje, na przykład typografia, wymyślne style -->

### Nadmierne zagnieżdżanie selektorów

Jeśli twój selektor wygląda tak:
```css
div.post-body.view.view--loaded > div.post-body__body > div > p:nth-child(35) {
        color: red;
}
```

to każda zmiana w HTML, sprawi, że przestanie on działać. Selektory nie powinny być zagnieżdżone bardziej niż do 2 - 3 elementów, a jeśli jest ich więcej, znacznie rośnie wysiłek związany ze zrozumieniem kodu.

Warto na to zwracać szczególną uwagę, podczas korzystania z preprocesorów CSS, które ułatwiają tworzenie zagnieżdżeń.
Mniejsza ilość zagnieżdżeń w kodzie, to także szybsze działanie przeglądarki użytkownika, ponieważ ma ona do przeparsowania, mniejszą ilość selektorów. 
Zapoznaj się z pseudoselektorami CSS, ponieważ pozwalają one na bardziej eleganckie stylowanie. 

### Ogólny bałagan w arkuszach stylów

Arkusze CSS potrafią się bardzo szybko rozrastać, co prowadzi do sytuacji, w której coraz trudniej jest dodawać lub zmieniać konkretne wartości. Wzrost złożoności kodu, to jeden z najgorszych wrogów programisty, dlatego powinieneś konsekwentnie dbać o porządek w arkuszach. 

Kilka porad:
* Utrzymuj logiczny podział stylów - arkusz możesz podzielić komentarzami na sekcje, odnoszące się do różnych elementów
* Przed dodaniem nowego znacznika CSS lub wykorzystaniem klasy już dodanej w HTML, przeszukaj cały arkusz stylów i sprawdź, czy nie możesz rozbudować już istniejącego selektora. Nie ma sensu dodawanie go ponownie, jeśli już istnieje.
* Zapoznaj się z metodologiami tworzenia CSS, takimi, jak BEM czy SMACSS.
* W większym projekcie, rozważ zastosowanie preprocesora CSS, który umożliwia rozdzielenie kodu na kilka arkuszy, łączących się w jeden po kompilacji. 
* Innym rozwiązaniem, jest podział kodu CSS na kilka arkuszy, które są następnie załączane do html, gdy są potrzebne. Takie rozwiązanie jest wygodne, ale zwiększa ilość czasochłonnych requestów http do serwera. 

### Niepotrzebne zapobieganie wrapowaniu tekstu
Przez to wyłazi na innych rozdzielczościach

### Tworzenie designu pixel perfect z myślą tylko o swoim ekranie.
### Brak myślenia o dynamicznym zachowaniu strony
        * Gdy dodamy więcej treści
        * Gdy zmieni się rozdzielczość strony 
        * inne rozwiązania "ad hoc"
### Nieprawidłowe wcinanie wierszy

### Niespójne nazewnictwo
Mieszanie różnych języków

### Zostawianie zakomentowanego kodu
### Różne sposoby stylowania takich samych elementów
### Osobne stylowanie elementów w jednej grupie (kilka margin top, zamiast jednego dla wrapa)
### Stylowanie, gdy markup html jest do poprawy

Przykładowo, w kodzie znajdują się dwa elementy, mające służyć jako linie, oddzielające poszczególne elementy. Mają one mieć taką samą długość.
```html
<div class="row">
    <hr>
</div>

<!-- drugi element -->
<div>
    <hr>
</div>
```
Gdy klasa .row, nadaje elementom dodatkowy margines, padding lub długość, uzyskanie prawidłowej struktury html, będzie wymagało kombinowania. Lepiej jest najpierw naprawić strukturę HTML (o ile można). Ostylowanie tych dwóch elementów, zajmie wtedy znacznie mniej czasu. 
