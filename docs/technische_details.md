# Technische Details

- IServ Modul: Mediotheken (<https://angelaschule-osnabrueck.net/iserv/legacy/mlibrary>)
- Type-And-Search sind GET-Request mit JSON-Response über: `mlibrary\search_auto.php`
  ```
  https://angelaschule-osnabrueck.net/idesk/mlibrary/search_auto.php?term%5Bmlibrary%5D=Bibliothek&term%5Bskey%5D=Rowling&term%5Bhowsearch%5D=field1=
  ```

  ```json
  [{"value":"Rowling, J. K."},{"value":"Rowling, J.K."},{"value":"Rowling, J. K. (Verfasser) Fritz, Klaus (\u00dcbersetzer)"},{"value":"Rowling, J. K. (Verfasser) Fritz, Klaus (\u00dcbersetzer) Kay, Jim (Illustrator)"},{"value":"Rowling, J.K. (Verfasser) Fritz, Klaus (\u00dcbersetzer) Kay, Jim (Illustrator)"},{"value":"Rowling, J. K. (Verfasser) Tiffany, John (Verfasser) Thorne, Jack (Verfasser) Fritz, Klaus (\u00dcbersetzer) Hansen-Schmidt, Anja (\u00dcbersetzer)"},{"value":"Rowling, Joanne K."},{"value":"Rowling, K."}]
  ```

- Suche über: `mlibrary/search.php`

  ```
  https://angelaschule-osnabrueck.net/idesk/mlibrary/search.php?data%5Bhow_search1%5D=field1&data%5Bvalue1%5D=Rowling&data%5Bin_mlibrary%5D=Bibliothek&mlibrary=Bibliothek&data%5Bsearch%5D=Suche+starten&data%5Bsearch%5D=Suchen&data%5Bbackref%5D=
  ```
- Funde werden als HTML zurückgeliefert.

## Idee

- Restartige Schnittstelle mit lesendem Zugriff auf Datenbank
- Einfachen webbasierten responsiven und reaktiven Client
- Client als IFRAME in IServ einbindbar, quasi als "Modul"
- Technologie-Vorschlag: Mikro-Dienst in Go, WebClient in vuejs / vuetify
- Benötigt Zugang zu IServ-Server, Logging der PostgreSQL-Ebene anhand der Client-Anfragen könnte schon reichen. Ggf. Blick in php-Quelltext hilfreich

- Ggf. Stand-Alone-Anwendung möglich?