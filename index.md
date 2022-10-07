# Programmieren einer Webapp für Teamverwaltung und Projektplanung

Eine Maturaarbeit von Rafael Urben

## Abstract

## Vorwort

## Inhaltsverzeichnis

## 1. Einleitung

### Ausgangslage

### Ziel der Arbeit

## 2. Theorie

Webseiten sind für einen grossen Teil der Menschheit etwas, mit dem sie täglich konfrontiert werden. Doch viele wissen eigentlich gar nicht, worum es sich dabei handelt und wie sie funktionieren. In diesem Theorieteil wird die Funktionsweise einer Webseite deshalb für eher unerfahrene Benutzer von Grund auf erarbeitet. Für detailliertere Beschreibungen und verwendete Software wird hierbei auf Kapitel 3 verweisen.

### Was sind Webseiten?

Bei einfachen Webseiten handelt es sich vereinfacht gesagt um eine Sammlung von Textdateien, welche irgendwo auf dieser Welt gespeichert sind und über das Internet der ganzen Welt zur Verfügung gestellt werden werden. Webseiten können aber, wie es bei jeglichen anderen Dateien der Fall ist, auch lokal gespeichert werden. Dann entfällt jedoch nur die Reise um die halbe Welt, die Funktionsweise bleibt gleich: Die Webseite wird nach Abrufen im Browser (auch «web browser» oder «internet browser» genannt) dem Benutzer angezeigt. Der Browser ist auch für alle Benutzerinteraktionen zuständig.

#### Client und Server

Im Bereich der Informatik wird häufig von Clients (_engl._ «client»: Kunde) und Servern (_engl._ «server»: Diener) gesprochen. Als Client wird dabei der Rechner bezeichnet, welcher eine Anfrage lokal oder über das Internet an einen Server stellt. Der Server ist dementsprechend der Rechner, welche die Anfrage erhält und bearbeitet. Das Wort «Rechner» steht hierbei für das Gerät, welches für die Anfrage zuständig ist. Es kann sich dabei also um einen Personal Computer (PC) handeln, kann aber auch für ein Smartphone, eine Smartwatch oder sogar einen intelligenten Kühlschrank stehen. Dies gilt nicht nur für den Client, sondern auch für den Server. Denn alle Geräte, welche sich mit einem Netzwerk verbinden können, können sowohl als Client als auch Server agieren. Bei Servern selbst handelt es sich meistens jedoch um grössere Anlagen, welche dazu ausgelegt sind, Millionen von Anfragen in der Minute zu bearbeiten. Von den Komponenten her betrachtet sind diese jedoch einem Computer bis auf wenige Details sehr ähnlich. Je nach Kontext kann das Wort Client auch für das spezifische Programm, welches die Anfrage ausführt oder den Menschen hinter dem Gerät stehen.

#### Requests und HTTP(S)

Jedes mal, wenn eine Webseite geöffnet wird oder auf eine neue Seite navigiert wird, löst der Browser eine Anfrage (_request_) aus. Diese wird über HTTP(S) an den Server gesendet, welcher mit einer _response_ (_engl_. für Antwort) reagiert. HTTP steht hierbei für «Hypertext Transfer Protocol». Das angehängte «S» steht für «secure», also sicher. Diese beiden Protokolle sieht man häufig in der Adressleiste des Browsers und bei Links, da es sich dabei um das für Webseiten verwendete Protokoll handelt. Ähnlich wie eine Dateiendung gibt das Protokoll an, wie die Daten formatiert sind, damit der Server weiss, welches Programm die Anfrage zu bearbeiten hat. Es gibt auch viele andere Protokolle, darunter FTP («File Transfer Protocol») oder SSH («Secure Shell»). Grundsätzlich kann jede Applikation ihr eigenes Protokoll verwenden, sowohl über das Internet als auch lokal. Die Einstellungen auf Windows-Geräten zum Beispiel können mit dem MS-SETTINGS-Protokoll angesprochen werden. So öffnet [ms-settings:windowsupdate](ms-settings:windowsupdate) ^[https://docs.microsoft.com/en-us/windows/uwp/launch-resume/launch-settings-app#update-and-security] die Seite für Windows-Updates. 

##### Die Täuschung hinter HTTPS

**Achtung aufgepasst!** Betreffend HTTPS gibt es im Internet und in der Gesellschaft sehr gefährliches Halbwissen. Obwohl das s für sicher steht, heisst dies **nicht**, dass eine Webseite auch sicher ist. Dies bedeutet nur, dass die Verbindung vom Client zum Server verschlüsselt ist. Jede und jeder kann heutzutage ein sogenanntes SSL-Zertifikat («Secure Socket Layer») erhalten und somit eine verschlüsselte Verbindung zum eigenen Server ermöglichen. Auch wenn eine Webseite also ein Schloss-Symbol in der Adressleiste hat, kann sie von einem Scammer stammen, der an Daten der Benutzer gelangen will. Wer ein wenig sicherer gehen will, kann in den gängigen Browsern via Klick auf das Schloss-Symbol weitere Informationen über das verwendete Zertifikat erhalten, z. B. wann und von wem es ausgestellt wurde.

##### Die Unsicherheit hinter HTTP

HTTP ist seit dem Aufkommen von HTTPS aufgrund seiner mangelnden Verschlüsselung aus der Mode gekommen. Da die Verbindung zu einer Webseite über HTTP nicht verschlüsselt ist, kann die Anfrage auf dem Weg zum Server über eine Man-in-the-middle-Attacke angefangen und mitgelesen werden. Bei HTTPS ist dies dank der Verschlüsselung nicht mehr der Fall. Passwörter und sensible Daten sollten nie über HTTP übertragen werden.

#### Domains und URLs

Wenn eine Webseite geöffnet werden soll, welche nicht auf demselben Gerät gespeichert ist, muss die Anfrage irgendwie an den zuständigen Server gelangen. Hier kommt nun das World-Wide-Web (WWW; Internet) ins Spiel. Wer eine Webseite öffnen will, hat meistens etwas folgender Art: `https://www.youtube.com/watch?v=dQw4w9WgXcQ`. Dies ist eine sogenannte URL («Uniform Resource Locator») und besteht aus verschiedenen Teilen. Der erste Teil, `https`, steht, wie wir bereits wissen, für das Protokoll. Der zweite Teil, `www.youtube.com`, ist die Domain und der letzte Teil, alles ab dem dritten Schrägstrich («Slash») ist der Pfad. 

##### Domain

Die Domain ist der mehr oder weniger wichtigste Teil einer URL, denn Sie bestimmt den Zielserver. Sie besteht aus folgenden Teilen und wird von rechts nach links immer spezifischer:

- «Top-level Domain» (TLD)
- «Second-level Domain» (SLD)
- «Third-level Domain», «Fourth-level Domain» usw.

Die TLD-Endung gibt meistens Informationen darüber, in welchem Land sich eine Webseite «befindet» oder zu welcher Kategorie eine Webseite gehört. (z. B. `.ch`, `.com`, `.gov`) Bis auf einige Ausnahmen (z. B. `.swiss` ^[https://www.hostpoint.ch/domains/swiss.html#domswiss5]) haben TLDs jedoch keine bestimmten Richtlinien, wer eine Domain unter dieser TLD mieten darf. Die SLD ist der eigentliche Hauptteil der Domain. In unserem Beispiel wäre dies `.youtube.com`. Bei mehrteiligen Domainendungen (z. B. `.co.uk`) ist dementsprechend die «Third-level Domain» der Hauptteil und der Rest um eine Stufe verschoben. Dies ist auch der Teil, welcher in E-Mails unbedingt immer beachtet werden muss. Weitere Subdomains gehören jeweils zur entsprechenden Hauptdomain und sind auch im Besitz deren Inhaber. Für Webseiten wird üblicherweise die Subdomain `www.`, also in unserem Beispiel `Www.youtube.com` verwendet. Dies ist jedoch nicht zwingend und wird mittlerweile eher als Erkennungsmerkmal verwendet.

`localhost` ist ausserdem eine Pseudo-Domain, welche immer auf das aktuelle Gerät zurückverweist.

##### Pfad

Der Pfad, also in unserem Beispiel `/watch?v=dQw4w9WgXcQ`, gibt dem Server an, auf welche Resource zugegriffen werden will. Bei einer sicheren Verbindung wird der Pfad auch verschlüsselt und bleibt somit für Zwischenstellen verborgen.

##### Anfrage

Um herauszufinden, welcher Server hinter einer Domain steckt, fragt das anfragende Gerät bei sogenannten DNS («Domain Name System») Servern nach. Diese geben dann eine IP-Adresse retour. Diese identifiziert ein Gerät in einem Netzwerk eindeutig. An diese IP-Adresse wird schliesslich die HTTP(S) request gesendet.

Informationen über die Funktionsweise von IP-Adressen können [WikiPedia](https://de.wikipedia.org/wiki/IP-Adresse) entnommen werden.

#### Dynamische und statische Webseiten

Bei Webseiten gibt es eine wichtige Unterscheidung: Statische und dynamische Webseiten. Statische Webseiten ändern ihren Inhalt grundsätzlich nicht. Ein Client greift dabei fast direkt auf die Dateien zu, ohne dass ein Server diese zuerst modifiziert. Sie sind auch für alle Besucher identisch (Beispiel: Dokumentation eines Computerprogrammes). Ganz anders funktionieren dynamische Seiten: Hier modifiziert der Server die Webseite für jeden Benutzer individuell. Auch kann sich der Inhalt von Aufruf zu Aufruf unterscheiden.
Jede Webseite, welchen Benutzern das Einloggen oder Interagieren mit anderen Benutzern ermöglicht, ist somit sicher eine dynamische Webseite. Nur weil eine Webseite aber interaktiv ist, bedeutet dies nicht automatisch, dass sie auch dynamisch ist.

### Was sind native Apps und Webapps?

In diesem Abschnitt geht es um den Unterschied zwischen sogenannten nativen Applikationen und Webapplikationen.

#### Native App

Native Apps sind auf ein bestimmtes Betriebssystem zugeschnitten und funktionieren exakt so nicht in anderen Betriebssystemen. Diese Apps können auf diverse Funktionen des Betriebssystems zugreifen und sich zum Beispiel mit Widgets in diverse Teile des Betriebssystems integrieren und können auf den lokalen Speicher zugreifen. Sie werden grundsätzlich über den für das Betriebssystem eigenen Store installiert (App Store, Google Play Store, Microsoft Store) oder in einem für das OS («Operating System», Betriebssystem) bekannten Format (z. B. `.msi` und `.exe` für Windows, `.apk` für Android) aus dem Internet heruntergeladen und installiert. Native Apps können sowohl ausschliesslich auf dem lokalen Gerät laufen als auch mit einem Server kommunizieren.

#### Webapp

Eine Webapp ist eine dynamische Webseite, welche mit diversen Funktionen Interaktionen ermöglicht. Die Daten (z. B. Speicherstand) werden auf einem Server gespeichert und verarbeitet und können dadurch von verschiedenen Geräten aus zugegriffen werden. Eine solche App erfordert keine Installation, jedoch eine durchgehende Internetverbindung. Authentifizierungs- und Trackinginformationen werden, sofern relevant, in sogenannten Cookies im Browser gespeichert. Webapps können, wenn sie responsiv (_engl._ «responsive»: reaktionsfähig) sind, auf Smartphones und PCs mit unterschiedlichen Bildschirmgrössen verwendet werden.

#### Die Probleme

Während für viele Funktionen (z. B. NFC, Netzwerkzugriff) native Apps zwingend benötigt werden, ist nicht für alle Betriebssysteme eine separate App zu entwickeln für die meisten Entwickler ein massgebliches Argument für Webapps. Dies spart erheblich Aufwand und Kosten und ermöglicht ein viel grösseres Zielpublikum. Jedoch fühlen sich Webapps nicht wirklich wie Apps an. Man befindet sich immer noch im Browser und sieht die ganze Zeit die Adressleiste sowie diverse andere Steuerelemente. Nicht nur benötigen diese auf Smartphones viel Platz, sondern sie können auch zu versehentlicher Bedienung führen oder Inhalte der Webapp überdecken.

#### PWAs - die Kombination

Aus diesen Gründen wurden PWAs («Progressive Web Apps») ins Leben gerufen. Diese sind, wie der Name erwarten lässt, immer noch Webapps. Jedoch haben sie – besonders für Smartphones – einige wichtige Erweiterungen. PWAs können zum Home-Bildschirm hinzugefügt werden. Dort sehen sie wie jede andere App aus und auf den ersten Blick gibt es keinen Unterschied, denn sie starten – sofern richtig konfiguriert – im Vollbildmodus ohne die oben erwähnten Browser-Navigations-Buttons. Je nach Betriebssystem und Konfiguration können PWAs sogar in der Lage sein, offline zu funktionieren.

### Was macht eine Webseite aus?

Eine Webseite als Gesamtpaket besteht aus zwei Teilen: dem Frontend und dem Backend.

#### Backend

Unter Backend wird alles verstanden, was auf dem Server abläuft, respektive ausserhalb des Einflussbereichs des Clients passiert. Während die Aufgaben des Backends bei statischen Seiten nur die Auslieferung von Dateien beinhaltet, spielt das Backend bei dynamischen Seiten eine grosse Rolle. Hier findet die Authentifizierung des Clients statt, es werden Berechnungen durchgeführt und die Seite wird für den Client vorbereitet. Nach der Verarbeitung einer _request_ sendet der Server schliesslich eine _response_ als Antwort.

#### Frontend

Das Frontend beinhaltet alles, was auf der Clientseite abläuft. Vom Aussehen der Webseite bis zur Benutzerinteraktion ist hier alles dabei. Im Frontend gibt es drei Programmier- und Auszeichnungssprachen, welche verwendet werden: HTML, CSS und JavaScript

##### HTML - das Gerüst

Der Inhalt einer normalen HTTP response besteht aus HTML («HyperText Markup Language»). HTML ist nicht direkt eine Programmiersprache, sondern eine Auszeichnungssprache (_engl._ «markup language») ^[https://de.wikipediacom/wiki/Auszeichnungssprache]. Sie definiert eine Hierarchie der Elemente einer Webseite sowie deren Eigenschaften und Grundformatierungen. Sie besteht aus Tags (_engl._ «tag»: Etikett), welche an den grösser als und kleiner als Zeichen erkennt werden können.

```html
<!DOCTYPE html>
<html>
	<head>
		<title>Ich bin eine Webseite!</title>
	</head>
	<body>
	</body>
</html>
```

##### CSS - die Fassade

##### JavaScript - die Technik


## 3. Durchführung

## 4. Resultate

## 5. Diskussion

## Dank

## Verzeichnisse

## Schlusswort

## Eigenständigkeitserklärung

Ich erkläre hiermit, dass ich diese Arbeit selbständig verfasst und keine anderen als die angegebenen Quellen benutzt habe. Mir ist bekannt, was ein Plagiat ist und ich bin mir der Konsequenzen eines Teil- oder Vollplagiates bewusst.

## Anhang
