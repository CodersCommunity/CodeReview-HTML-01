# Code Review kursu HTML#1

Film: https://www.youtube.com/watch?v=k2IydkL3EOs

Temat: http://forum.pasja-informatyki.pl/125794/cr-html-%231-tworzenie-stron-www-pierwszy-projekt-wiedza-podstawowa

---

Ten branch zawiera poprawki dotyczące samego kodu HTML. Tak, **wygląd strony się zmienił**, ale – z racji tego, że mówimy o kursie HTML – nie dodaję żadnego CSS-a.

---

## Lista poprawek

_Rzeczy zmienione, a oznaczone jako **preferencja** są po prostu moimi osobistymi preferencjami co do kodu HTML i nie są lepsze/gorsze od pierwotnego sposobu; są po prostu inne._

### Ogólne

* Zmieniłem wcięcia w kodzie na IMO czytelniejsze (**preferencja**).
* Usunąłem zamknięcie XML-owego ze znaczników bez zamknięcia (**preferencja**).
* Zmieniłem nazwę `html` na wersję pisaną małymi literami w `DOCTYPE` (**preferencja**).
* Zmieniłem nazwę kodowania na `UTF-8` (**preferencja**, choć dawniej [walidator się tego czepiał](http://tutorials.comandeer.pl/html5-blog.html#ustawienie-kodowania)).

### `head`

* Przeniosłem `meta[http-equiv="X-UA-Compatible"]` tuż po `meta[charset]` i **zostawiłem** te tagi jako pierwsze w `head` – wszystko z powodu [znanych bugów](https://github.com/h5bp/html5-boilerplate/blob/b5d6e7b1613fca24d250fa8e5bc7bcc3dd6002ef/dist/doc/html.md#the-order-of-the-title-and-meta-tags).
* Usunąłem z `meta[http-equiv="X-UA-Compatible"]` fragment `,chrome=1`, gdyż Chrome Frame [nie istnieje od lat](http://blog.chromium.org/2013/06/retiring-chrome-frame.html).

### `body`

* Zostawiłem stronę bez dodawania znaczników sekcjonujących HTML5 (`article`) czy znacznika `main` – jest to na tyle prosta strona, że nie ma potrzeby dodatkowo jej "spulchniać".
* Z racji tego, że _de facto_ mamy tutaj do czynienia z podziałem filmów na kategorie, to badzo dobrze nadaje się do tego [lista klucz-wartość (`dl`)](https://www.w3.org/TR/html5/grouping-content.html#the-dl-element), gdzie kluczem (`dt`) jest nazwa kategorii, a wartościami (`dd`; w tym przypadku mamy tylko po jednym filmie w kategorii, ale można ich umieścić więcej) – poszczególne filmy. Można się pokusić o zrobienie tego przy pomocy sekcji (`section`), gdzie każda kategoria byłaby odrębną sekcją, jej nazwa – nagłówkiem (w naszym wypadku `h2`), a same filmy – umieszczone w liście (`ul`) czy, jeśli dołączony byłby także ich opis, podsekcjami (`section > section`) z nagłówkiem. Niemniej `dl` IMO pasuje tutaj o wiele bardziej i nie ma potrzeby tworzyć dodatkowych sekcji.
* Zamiast dwóch linków, sąsiadujących ze sobą i prowadzących do tej samej strony, stworzyłem z nich jeden (co może mieć np. wpływ na czytniki ekranowe). Dodatkowo usunąłem odstępy stworzone przy pomocy `br`, gdyż tego typu rzeczy należy robić w CSS.
* Z racji tego, że drugiego linka już nie ma, przeniosłem jego `[title]` bezpośrednio na obrazek.
* **Każdy** obrazek **MUSI** mieć `[alt]`. Jeśli jest to obrazek dekoracyjny lub dublujący informacje z kontekstu, `[alt]` [**MUSI** być pusty](https://www.w3.org/TR/html5/embedded-content-0.html#a-graphical-representation-of-some-of-the-surrounding-text). Tak jest w tym wypadku: w linku jest już zawarta nazwa filmu, a screen z niego nie niesie żadnej istotnej, dodatkowej informacji (IMO to ozdobnik upiększający listę). Jeśli jednak kadr uzna się za istotny, należałoby opisać, co przedstawia.
* Usunąłem `[target]`, bo to [średni pomysł](https://kornel.ski/pl/target).
