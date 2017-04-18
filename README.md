# Scoutk�ren G�ta Lejon n�rvaro


En fork av Skojjt som �r utvecklad av Martin Green/Tynnereds scoutk?r.
https://github.com/martin-green/skojjt

Ni kommer �t n�rvaron p�:
https://gotalejon-narvaro.appspot.com

M�let med skojjt �r en enkel n�rvaroregistrering som kan anv�nds av alla p� avdelning. Samt att g�ra rapporteringen enkel (ingen excel).
Alternativen verkar s� underm�liga f�r v�r verksamhet, s� ett eget system var den b�sta m�jligheten.
Man ska kunna g�ra sin registering direkt n�r man har m�tet.
Det finns en direktkoppling till v�rt eget medlemsregister, scoutnet. Vi kan synkronisera nya medlemmar direkt fr�n scoutnet med en knapptryckning.
Det �r en web-site som fungerar i mobiltelefon, inget behov av en app. Det ser ut som en app i telefonens browser.
Den hostas p� Google app engine. Vilket ger f�ljande f�rdelar:
* Google st�r f�r s�kerheten. Anv�ndarna loggar in med sina google konton. Administrat�ren s�tter access i skojjt, sen kan dom registrera.
* google st�r f�r SSL certifikatet. All trafik g�r via https.
* Drifts�kerheten �r god.
* Det �r gratis upp till en viss gr�ns f�r trafik och datam�ngd (mer memcache beh�vs, f�r att begr�nsa data l�sningar).
* Om det skulle bli m�nga anv�ndare s� klarar googles servrar det.

Det finns rapportering av n�rvaro per grupp (avdelning) som G�teborgs kommun kr�ver.
Vi har �ven m�jlighet att koppla denna n�rvaro till andra partners, t ex Sensus studief�rbund.

Skojjt implementerar DAK f�r redovisning till G�teborgs kommun:
http://www.sverigesforeningssystem.se/dak-formatet/vad-ar-dak/

###[Dokumentation](https://github.com/martin-green/skojjt/wiki)


###Hur man testar/utvecklar i Windows:
* Klona git-repon till lokal dator.
* Installera Python 2.7 och Google App Engine SDK (GAE).
* Starta GAE. L�gg till skojjt med File|Add existing application...
* Markera skojjt i listan kicka start, sen browse.
* Man kan ocks� k�ra Visual Studio Code f�r att f� brytpunkter i koden.

###Hur man testar/utvecklar i Linux:
* Klona git-repon till lokal dator.
* Installera Python 2.7 och Google App Engine SDK (GAE). 
* Konfigurera GAE `gcloud init
* Deploy kod `gcloud app deploy` från git mappen
* Testa appen `gcloud app browse`

#### K�nda fel
Om du k�r p� windows och f�r felet:
"ImportError: cannot import name RAND_egd"

Editera:
C:\Program Files (x86)\Google\google_appengine\google\appengine\dist27\socket.py

ta bort: RAND_egd från rad 73:   
from _ssl import RAND_add, RAND_egd, RAND_status, SSL_ERROR_ZERO_RETURN, SSL_ERROR_WANT_READ, SSL_ERROR_WANT_WRITE, SSL_ERROR_WANT_X509_LOOKUP, SSL_ERROR_SYSCALL, SSL_ERROR_SSL, SSL_ERROR_WANT_CONNECT, SSL_ERROR_EOF, SSL_ERROR_INVALID_ERROR_CODE
