A JS Webapp for renting and lending out things.
A Group Project for Web Programming class with Juli-Afk and Shank404



-------------------------------NPM-Install----------------------------------------------------------------------------------------
npm install express, node, bcrypt, cookie-parser, formidable, sqlite3, fs, path
-------------------------------Server Starten-------------------------------------------------------------------------------------
node server.js
-------------------------------Curl-Commands--------------------------------------------------------------------------------------
***LOGIN-COMMAND***
curl http://localhost:8000/api/authenticate/login -X POST -d "username=MaxMustermann1" -d "password=123"
=> Erhaltene SessionID zwischenpeichern

***Gegenstand einstellen***
=> Bitte Cookie SessionID einfügen !
curl http://localhost:8000/private/api/items/MaxMustermann1 -b "SessionID=BITTE_ANPASSEN;Username=MaxMustermann1" -F cli=true -F name=PKW-Anhaenger -F description=Ausgelegt_bis_4t -F provider=MaxMustermann1 -F lentTo= -F loanable=true -F borrowedtime=8 -F image=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAUAAAAFCAYAAACNbyblAAAAHElEQVQI12P4//8/w38GIAXDIBKE0DHxgljNBAAO9TXL0Y4OHwAAAABJRU5ErkJggg==

***Gegenstand aktualisieren***
=> Bitte Cookie SessionID einfügen !
=> ID des Artikels anpassen, wenn mehr als ein Artikel erstellt wird.
curl http://localhost:8000/private/api/items/1 -X PUT -b "SessionID=BITTE_ANPASSEN;Username=MaxMustermann1" -F cli=true -F name=PKW-Anhaenger -F description=Ausgelegt_bis_4t_mit_Papieren_nur_gegen_Kuchen -F image=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVR42mN0/8VQDwAEkwHCl9P0HAAAAABJRU5ErkJggg==

***Details eines Gegenstandes ausgeben***
=> Bitte Cookie SessionID einfügen !
=> ID des Artikels anpassen, wenn mehr als ein Artikel erstellt wird.
curl http://localhost:8000/private/api/items/1 -X GET -b "SessionID=BITTE_ANPASSEN;Username=MaxMustermann1"

***Gegenstand löschen***
=> Bitte Cookie SessionID einfügen !
=> ID des Artikels anpassen, wenn mehr als ein Artikel erstellt wird.
curl http://localhost:8000/private/api/items/1 -X DELETE -b "SessionID=BITTE_ANPASSEN;Username=MaxMustermann1"

***Gegenstand ausleihen***
=> Bitte Cookie SessionID einfügen !
=> ID des Artikels anpassen, wenn mehr als ein Artikel erstellt wird.
=> Doppelter QueryString bitte den Namen des Ausleihenden ggf. anpassen bei Abweichung.
curl http://localhost:8000/private/api/borrow/1/MaxMustermann1 -X POST -b "SessionID=BITTE_ANPASSEN;Username=MaxMustermann1"

***Gegenstand zurückgeben***
=> Bitte Cookie SessionID einfügen !
=> ID des Artikels anpassen, wenn mehr als ein Artikel erstellt wird.
curl http://localhost:8000/private/api/return/1 -X POST -b "SessionID=BITTE_ANPASSEN;Username=MaxMustermann1"

