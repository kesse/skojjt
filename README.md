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

Skojjt implementerar APN/DAK f�r redovisning till G�teborgs kommun:

http://www.sverigesforeningssystem.se/dak-formatet/vad-ar-dak/
http://ukf.umea.se/aktivitetskort

### [Dokumentation](https://github.com/martin-green/skojjt/wiki)

### Hur man testar/utvecklar i Windows:
* Klona git-repon till lokal dator.
* Installera Python 2.7 och Google App Engine SDK (GAE). 
	https://storage.googleapis.com/appengine-sdks/featured/GoogleAppEngine-1.9.73.msi
* Starta GAE. L�gg till skojjt med File|Add existing application...
* Markera skojjt i listan kicka start, sen browse.
* Man kan ocks� k�ra Visual Studio Code f�r att f� brytpunkter i koden.

### Hur man testar/utvecklar i Linux:
* Klona git-repon till lokal dator.
* Installera Python 2.7 och Google App Engine SDK (GAE). 
* Konfigurera GAE `gcloud init`
* Deploy kod `gcloud app deploy` fr�n git mappen
* Testa appen `gcloud app browse`


### Hur man testar/utvecklar p� Mac:
* Anv�nd homebrew f�r att installera Python 2.7 och Google App Engine.
    + Installera homebrew om inte redan gjort 
    + Installera python2 i homebrew
    + Installera Google App Engine (ligger i en cask eftersom den �r bin�r)
        - `brew cask info google-cloud-sdk`
        - `brew tap caskroom/cask`
        - `brew cask install google-cloud-sdk`
        - `source /usr/local/Caskroom/google-cloud-sdk/latest/google-cloud-sdk/path.bash.inc`
        - `source /usr/local/Caskroom/google-cloud-sdk/latest/google-cloud-sdk/completion.bash.inc`
* Konfigurera GAE `gcloud init`
* K�r lokal test-server och admin f�nster:
  + `dev_server.py app.yaml`
  + `open http://localhost:8080`
* Deploy projektet `skojjt-X`(ditt val av namn)
  + `gcloud app deploy index.yaml --project skojjt-X`
  + `gcloud app deploy app.yaml --project skojjt-X`
* Testa appen `gcloud app browse`
