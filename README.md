# Code Review kursu HTML#1

Film: https://www.youtube.com/watch?v=k2IydkL3EOs

Temat: http://forum.pasja-informatyki.pl/125794/cr-html-%231-tworzenie-stron-www-pierwszy-projekt-wiedza-podstawowa

---

Ten branch zawiera dodatkową poprawkę ponad [branch `refactor`](https://github.com/CodersCommunity/CodeReview-HTML-01/tree/refactor).

---

## Poprawka

_Ta poprawka jest przeznaczona **wyłącznie** dla serwera Apache. Wersje dla innych serwerów można znaleźć w [organizacji H5BP na GitHubie](https://github.com/h5bp?utf8=%E2%9C%93&query=server-configs-)._


Zgodnie ze [specyfikacją HTML5](https://www.w3.org/TR/html5/document-metadata.html#other-pragma-directives), elementy`meta[http-equiv]` _de facto_ zastępują nagłówki HTTP:

 > […] must use a name that is identical to an HTTP header registered in the Permanent Message Header Field Registry, and must have behavior identical to that described for the HTTP header.

Dlatego też można (a wręcz **należy**!) przenieść ustawienie trybu kompatybilności dla IE do ustawień serwera, co dodatkowo [rozwiązuje kilka znanych problemów](https://github.com/h5bp/html5-boilerplate/blob/b5d6e7b1613fca24d250fa8e5bc7bcc3dd6002ef/dist/doc/html.md#x-ua-compatible).

Wypada także zauważyć, że tryb kompatybilności jest [zdeprecjonowany w IE 11](https://msdn.microsoft.com/library/bg182625.aspx#docmode) i [usunięty w Edge](https://blogs.windows.com/msedgedev/2015/05/06/a-break-from-the-past-part-2-saying-goodbye-to-activex-vbscript-attachevent/).

Ważny jest także fakt, że dołączanie `,chrome=1` jest niewskazane i bezsensowne, gdyż służyło włączaniu Chrome Frame (czyli dodatku odpalającego silnik Blink z Google Chrome'a w IE), który… [od lat nie istnieje](http://blog.chromium.org/2013/06/retiring-chrome-frame.html).
