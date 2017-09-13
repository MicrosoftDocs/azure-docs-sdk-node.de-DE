---
title: Node.js-Entwicklung mit Visual Studio Code und Azure
description: "Enthält ein umfassendes End-to-End-Tutorial zur Vorgehensweise beim Erstellen, Durchführen der Vorbereitung für Docker und Bereitstellen einer Node.js-App in Azure."
services: multiple
author: tomarcher
manager: douge
ms.service: azure-nodejs
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 06/25/2017
ms.author: joncart
ms.openlocfilehash: 1b43502394b7224c5791ee870999cdb958a0969d
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a>Node.js-Entwicklung mit Visual Studio Code und Azure

In diesem Tutorial wird veranschaulicht, wie Sie eine vorhandene Node.js-App (mit Docker) in einem Container anordnen und die App anschließend mit Visual Studio Code in Azure bereitstellen.

Für das Tutorial wird eine einfache To-Do-App genutzt, die von [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular) erstellt und veröffentlicht wurde. Da es sich hierbei um eine einseitige MEAN-App handelt, wird MongoDB als Datenbank, Node/Express für die REST-API bzw. den Webserver und Angular.js 1.x für die Front-End-Benutzeroberfläche verwendet. 

## <a name="prerequisites"></a>Voraussetzungen

Zum Durcharbeiten der Demo muss die folgende Software installiert sein:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Docker](https://www.docker.com/products/docker)
- [DockerHub-Konto](https://hub.docker.com/)
- [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [Azure-Konto](https://azure.microsoft.com/free/)
- [YARN](https://yarnpkg.com/en/docs/install)
- [Chrome](https://www.google.com/chrome/browser/desktop/): Wird verwendet, um das Front-End der Demo-App zu debuggen.
- MongoDB: Da für die Demo-App MongoDB verwendet wird, müssen Sie über eine lokal ausgeführte MongoDB-Instanz verfügen, die über den Standardport `27017` lauscht. Dies lässt sich am einfachsten erreichen, indem nach der Installation von Docker die folgenden beiden Befehle ausgeführt werden: `docker pull mongo` gefolgt von `docker run -it -p 27017:27017 mongo`.

## <a name="project-setup"></a>Projekteinrichtung

Laden Sie als Erstes das Beispielprojekt herunter, indem Sie die folgenden Schritte ausführen:

1. Öffnen Sie Visual Studio Code.

1. Drücken Sie **&lt;F1>**, um die Befehlspalette anzuzeigen.

1. Geben Sie an der Eingabeaufforderung der Befehlspalette `gitcl` ein, wählen Sie den Befehl **Git: Clone** aus, und drücken Sie die **&lt;EINGABETASTE>**.

    ![Befehl „gitcl“ in der Eingabeaufforderung der Befehlspalette von Visual Studio Code](./media/node-howto-e2e/git-clone.png)

1. Geben Sie `https://github.com/scotch-io/node-todo` ein, wenn Sie zum Eingeben der **Repository-URL** aufgefordert werden, und drücken Sie anschließend die **&lt;EINGABETASTE>**.

1. Wählen bzw. erstellen Sie das lokale Verzeichnis, in dem das Projekt geklont werden soll.

    ![Visual Studio Code-Explorer](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a>Integriertes Terminal

Da es sich um ein Node.js-Projekt handelt, müssen Sie zunächst sicherstellen, dass alle Abhängigkeiten des Projekts über npm installiert wurden.  

1. Drücken Sie **&lt;STRG>+'** (bzw. die entsprechende Tastenkombination für das deutsche Tastaturlayout), um das integrierte Terminal von Visual Studio Code anzuzeigen. 

1. Geben Sie `yarn` ein, und drücken Sie die **&lt;EINGABETASTE>**.  

    ![Ausführen des Befehls „yarn“ in Visual Studio Code](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a>Integrierte Git-Versionskontrolle

Nach der Installation der App-Abhängigkeiten per YARN wird die Datei `yarn.lock` erstellt, um auf einfache Weise dafür zu sorgen, dass später die gleichen Abhängigkeiten beschafft werden können. So wird ausgeschlossen, dass es in Bezug auf Continuous Integration-Builds, Produktionsbereitstellungen oder andere Entwicklercomputer zu Überraschungen kommt.

In den folgenden Schritten wird veranschaulicht, wie Sie die Datei `yarn.lock` in die Quellcodeverwaltung einchecken:

1. Wechseln Sie in Visual Studio Code zur integrierten Git-Registerkarte (die Registerkarte mit dem Git-Logo).

1. Geben Sie im Feld **Nachricht** eine Commit-Nachricht ein, und drücken Sie **&lt;STRG>+&lt;EINGABETASTE>**. 

    ![Hinzufügen der Datei „yarn.lock“ zu Git](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a>Projekt- und Codenavigation

Zur besseren Orientierung in der Codebase probieren wir nun einige Beispiele für die Navigationsfunktionen von Visual Studio Code aus.

1. Drücken Sie **&lt;STRG>+P**.

1. Geben Sie `.js` ein, um alle JavaScript/JSON-Dateien des Projekts mit dem jeweiligen übergeordneten Verzeichnis anzuzeigen. 

    ![Anzeigen aller JS-Dateien](./media/node-howto-e2e/git-output.png)

1. Wählen Sie `server.js` aus. Dies ist das Startskript für die App. 

1. Bewegen Sie den Mauszeiger auf die Variable **database** (in Zeile 6 importiert), um ihren Typ anzuzeigen. Diese Möglichkeit zum schnellen Prüfen von Variablen, Modulen und Typen in einer Datei ist bei der Entwicklung Ihrer Projekte sehr hilfreich. 

    ![Ermitteln des Typs](./media/node-howto-e2e/hover-help.png)

1. Wenn Sie mit der Maus in den Bereich einer Variablen – z.B. **database** – klicken, können Sie alle Verweise auf diese Variable anzeigen, die in der Datei enthalten sind. Um alle Verweise auf eine Variable für das gesamte Projekt anzuzeigen, klicken Sie mit der rechten Maustaste auf die Variable und wählen im Kontextmenü die Option **Alle Verweise suchen**.

    ![Suchen nach den Verweisen auf eine Variable](./media/node-howto-e2e/word-hilight.png)

1. Zusätzlich zum Zeigen auf eine Variable mit der Maus, um ihren Typ zu ermitteln, können Sie auch die Definition einer Variablen untersuchen. Dies ist sogar möglich, wenn sie sich in einer anderen Datei befindet. Klicken Sie hierzu mit der rechten Maustaste auf **database.localUrl** (Zeile 12), und wählen Sie im Kontextmenü die Option **Definition einsehen**. 

    ![Einsehen der Definition einer Variablen](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a>Ändern des Codes und Verwenden der automatischen Vervollständigung

Die MongoDB-Verbindungszeichenfolge ist in der Deklaration von **database.localUrl** hartcodiert. In diesem Abschnitt ändern Sie den Code, um die Verbindungszeichenfolge aus einer Umgebungsvariablen abzurufen, und machen sich mit dem AutoVervollständigen-Feature von Visual Studio Code vertraut.  

1. Öffnen Sie die Datei `server.js`.

1. Ersetzen Sie den folgenden Code: 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    durch diesen Code:

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

Beachten Sie Folgendes: Bei der manuellen Eingabe des Codes (anstelle von Kopieren und Einfügen) werden in Visual Studio Code die verfügbaren Elemente für die globale API des Node.js-**Prozesses** angezeigt, wenn Sie nach `process` den Punkt eingeben.

![Automatische Anzeige der API-Elemente bei AutoVervollständigen](./media/node-howto-e2e/process-env.png)

AutoVervollständigen funktioniert, weil von Visual Studio Code im Hintergrund TypeScript verwendet wird (auch für JavaScript). So werden Typinformationen angegeben, die dann während der Eingabe für die Vervollständigungsliste genutzt werden können. Visual Studio Code erkennt, dass es sich um ein Node.js-Projekt handelt, und die TypeScript-Typisierungsdatei für [Node.js wird automatisch von NPM heruntergeladen](https://www.npmjs.com/package/@types/node). Mit der Typisierungsdatei können Sie die automatische Vervollständigung auch für andere globale Node.js-Elemente, z.B. **Buffer** und **setTimeout**, sowie alle integrierten Module, z.B. **fs** und **http**, nutzen.

Diese automatische Beschaffung von Typisierungen funktioniert nicht nur für die integrierten Node.js-APIs, sondern auch für mehr als 2.000 Drittanbietermodule, z.B. React, Underscore und Express. Um beispielsweise zu verhindern, dass die Beispiel-App für Mongoose abstürzt, wenn keine Verbindung mit der konfigurierten MongoDB-Datenbankinstanz hergestellt werden kann, können Sie in Zeile 13 die folgende Codezeile einfügen:

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

Wie beim vorherigen Code auch, erhalten Sie die automatische Vervollständigung ohne jegliches Zutun.

![Automatische Anzeige der API-Elemente bei AutoVervollständigen](./media/node-howto-e2e/mongoose.png)

Sie können anzeigen, welche Module die automatische Vervollständigung unterstützen, indem Sie das Projekt [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) durchsuchen. Dies ist die von der Community gestützte Quelle aller TypeScript-Typdefinitionen.

## <a name="running-the-app"></a>Ausführen der App

Nachdem Sie den Code untersucht haben, können Sie die App ausführen. Drücken Sie **&lt;F5>**, um die App über Visual Studio Code auszuführen. Beim Ausführen des Codes mit **&lt;F5>** (Debugmodus) startet Visual Studio Code die App und öffnet das Fenster **Debugging-Konsole**, in dem die StdOut-Daten für die App angezeigt werden.

![Überwachen der StdOut-Daten einer App über die Debugging-Konsole](./media/node-howto-e2e/console.png)

Die **Debugging-Konsole** wird auch an die neu ausgeführte App angefügt, sodass Sie JavaScript-Ausdrücke eingeben können, die in der App ausgewertet werden. Außerdem ist die automatische Vervollständigung verfügbar. Geben Sie in der Konsole `process.env` ein, um dies in Aktion zu sehen:

![Eingeben von Code in der Debugging-Konsole](./media/node-howto-e2e/console-code.png)

Das Drücken von **&lt;F5>** zum Ausführen der App war möglich, da die derzeit geöffnete Datei eine JavaScript-Datei ist (`server.js`). Visual Studio Code nimmt daher an, dass es sich bei dem Projekt um eine Node.js-App handelt. Wenn Sie alle JavaScript-Dateien in Visual Studio Code schließen und dann **&lt;F5>** drücken, fragt Visual Studio Code die Umgebung ab:

![Angeben der Laufzeitumgebung](./media/node-howto-e2e/select-env.png)

Öffnen Sie einen Browser, und navigieren Sie zu `http://localhost:8080`, um die ausgeführte App anzuzeigen. Geben Sie eine Nachricht in das Textfeld ein, und fügen Sie einige Aufgaben hinzu (bzw. entfernen Sie sie), um ein Gefühl für die Funktionsweise der App zu erhalten.

![Ausgeführte To-Do-App](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a>Debuggen

In Visual Studio Code können Sie nicht nur die App ausführen und über die integrierte Konsole damit interagieren, sondern auch direkt im Code Breakpoints festlegen. Drücken Sie beispielsweise **&lt;STRG>+P**, um die Dateiauswahl anzuzeigen. Geben Sie in der Dateiauswahl `route` ein, und wählen Sie die Datei `route.js`.

Legen Sie in Zeile 28 einen Breakpoint fest. Dieser Breakpoint steht für die Express-Route, die aufgerufen wird, wenn die App versucht, einen To-Do-Eintrag hinzuzufügen. Klicken Sie zum Festlegen eines Breakpoints im Editor einfach auf den Bereich links von der Zeilennummer. Dies ist in der folgenden Abbildung dargestellt.

![Festlegen eines Breakpoints in Visual Studio Code](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> Neben Standard-Breakpoints unterstützt Visual Studio Code auch bedingte Breakpoints, mit denen Sie anpassen können, wann die Ausführung der App angehalten werden soll. Klicken Sie zum Festlegen eines bedingten Breakpoints mit der rechten Maustaste auf den Bereich links von der Zeile, in der Sie die Ausführung anhalten möchten. Wählen Sie dann **Bedingten Haltepunkt hinzufügen...**, und geben Sie entweder einen JavaScript-Ausdruck (z.B. `foo = "bar"`) oder eine Ausführungsanzahl an, um die Bedingung zu definieren, unter der die Ausführung angehalten werden soll.
> 
> 

Wechseln Sie nach dem Festlegen des Breakpoints zurück zur ausgeführten App, und fügen Sie einen To-Do-Eintrag hinzu. Das Hinzufügen eines To-Do-Eintrags bewirkt sofort, dass die Ausführung der App in Zeile 28 angehalten wird, in der Sie den Breakpoint festgelegt haben:

![Unterbrechung der Visual Studio Code-Ausführung an einem Breakpoint](./media/node-howto-e2e/debugger.png)

Nachdem die Anwendung angehalten wurde, können Sie den Mauszeiger auf die Ausdrücke des Codes bewegen, um ihren aktuellen Wert anzuzeigen, die lokalen Elemente bzw. Überwachungselemente und die Aufrufliste untersuchen und die Debug-Symbolleiste für den Schritt-für-Schritt-Durchlauf durch die Codeausführung verwenden. Drücken Sie **&lt;F5>**, um die Ausführung der App fortzusetzen.

## <a name="full-stack-debugging"></a>Full-Stack-Debuggen

Wie in diesem Thema bereits erwähnt wurde, ist die To-Do-App eine MEAN-App. Dies bedeutet, dass sowohl ihr Front-End als auch ihr Back-End mit JavaScript geschrieben wurden. Derzeit debuggen Sie den Back-End-Code (Node/Express), aber es kann sein, dass Sie später auch den Front-End-Code (Angular) debuggen müssen. Hierfür verfügt Visual Studio Code über ein umfangreiches Ökosystem mit Erweiterungen, z.B. integriertes Chrome-Debugging.

Wechseln Sie zur Registerkarte **Erweiterungen**, und geben Sie im Suchfeld `chrome` ein:

![Erweiterung zum Debuggen von Chrome in Visual Studio Code](./media/node-howto-e2e/chrome.png)

Wählen Sie die Erweiterung mit dem Namen **Debugger for Chrome** aus, und wählen Sie anschließend die Option **Installieren**. Wählen Sie nach der Installation der Erweiterung für das Chrome-Debugging die Option **Erneut laden**, um Visual Studio Code zu schließen und wieder zu öffnen und die Erweiterung so zu aktivieren. 

![Erneutes Laden von Visual Studio Code nach der Erweiterung für das Chrome-Debugging](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

Sie konnten den Node.js-Code ohne jegliche Visual Studio Code-spezifische Konfiguration ausführen und debuggen. Zum Debuggen einer Front-End-Web-App müssen Sie die Datei `launch.json` generieren, in der Visual Studio Code angewiesen wird, wie die App ausgeführt werden soll. 

Wechseln Sie zum Generieren der Datei `launch.json` zur Registerkarte **Debuggen**, klicken Sie auf das Zahnradsymbol (das mit einem kleinen roten Punkt versehen sein sollte), und wählen Sie die Umgebung **node.js** aus.

![Visual Studio Code-Option zum Konfigurieren der Datei „launch.json“](./media/node-howto-e2e/debug-gear.png)

Nach der Erstellung sieht die Datei `launch.json` etwa wie unten angegeben aus. Hiermit wird Visual Studio Code mitgeteilt, wie die App gestartet bzw. wie das Anfügen für das Debuggen durchgeführt werden soll. 

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "Launch Program",
            "program": "${workspaceRoot}/server.js"
        },
        {
            "type": "node",
            "request": "attach",
            "name": "Attach to Port",
            "address": "localhost",
            "port": 5858
        }
    ]
}
```

Beachten Sie Folgendes: Visual Studio Code hat erkannt, dass `server.js` das Startskript der App ist. 

Wählen Sie bei geöffneter Datei `launch.json` die Option **Konfiguration hinzufügen** (unten rechts) und anschließend die Option **Chrome: Launch with userDataDir** (Chrome: Mit userDataDir starten).

![Hinzufügen einer Chrome-Konfiguration zu Visual Studio Code](./media/node-howto-e2e/add-chrome-config.png)

Wenn Sie eine neue Laufzeitkonfiguration für Chrome hinzufügen, können Sie den JavaScript-Code des Front-Ends debuggen. 

Sie können den Mauszeiger auf alle angegebenen Einstellungen bewegen, um Dokumentation zum Zweck der Einstellung anzuzeigen. Beachten Sie auch, dass Visual Studio Code die URL der App automatisch erkennt. Aktualisieren Sie die **webRoot**-Eigenschaft in `${workspaceRoot}/public`, damit der Chrome-Debugger weiß, wo sich die Front-End-Objekte der App befinden:

```json
{
   "type": "chrome",
   "request": "launch",
   "name": "Launch Chrome",
   "url": "http://localhost:8080",
   "webRoot": "${workspaceRoot}/public",
   "userDataDir": "${workspaceRoot}/.vscode/chrome"
}
```

Um das Front-End und Back-End gleichzeitig zu starten oder zu debuggen, müssen Sie eine zusammengesetzte Laufzeitkonfiguration (*compound*) erstellen, damit Visual Studio Code weiß, welche Konfigurationssätze parallel ausgeführt werden sollen. 

Fügen Sie den folgenden Codeausschnitt als Eigenschaft der obersten Ebene in der Datei `launch.json` hinzu (als gleichgeordnetes Element der vorhandenen **configurations**-Eigenschaft).

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

Die Zeichenfolgenwerte, die im Array **compounds.configurations** angegeben sind, verweisen auf den Namen (**name**) der einzelnen Einträge in der Liste mit den Konfigurationen (**configurations**). Wenn Sie diese Namen geändert haben, müssen Sie die entsprechenden Änderungen im Array vornehmen. Wechseln Sie hierfür zur Registerkarte „Debuggen“, und ändern Sie die ausgewählte Konfiguration in **Full-Stack** (Name der zusammengesetzten Konfiguration). Drücken Sie anschließend **&lt;F5>**, um sie auszuführen.

![Ausführen einer Konfiguration in Visual Studio Code](./media/node-howto-e2e/full-stack-profile.png)

Durch die Ausführung der Konfiguration werden die Node.js-App (in der Ausgabe der Debugging-Konsole zu sehen) und Chrome (für die Navigation zur Node.js-App unter `http://localhost:8080`) gestartet.

Drücken Sie **&lt;STRG>+P**, und geben Sie `todos.js` ein (bzw. wählen Sie die Datei aus). Dies ist der Angular-Hauptcontroller für das Front-End der App. 

Legen Sie in Zeile 11 einen Breakpoint fest, der als Einstiegspunkt für einen neuen zu erstellenden To-Do-Eintrag dient.

Wechseln Sie zurück zur ausgeführten App, und fügen Sie einen neuen To-Do-Eintrag hinzu. Sie sehen, dass Visual Studio Code die Ausführung im Angular-Code angehalten hat.

![Debuggen des Front-End-Codes in Visual Studio Code](./media/node-howto-e2e/chrome-pause.png)

Wie beim Debuggen von Node.js auch, können Sie den Mauszeiger auf Ausdrücke bewegen, lokale Elemente bzw. Überwachungselemente anzeigen, Ausdrücke in der Konsole auswerten usw. 

Beachten Sie zwei interessante Punkte:

1. Im Bereich **Aufrufliste** werden zwei unterschiedliche Listen angezeigt: **Node** und **Chrome**. Außerdem wird angegeben, welche gerade angehalten ist.

1. Sie können zwischen dem Front-End- und Back-End-Code wechseln. Drücken Sie hierfür **&lt;F5>**, um die Ausführung zu starten und den Breakpoint zu erreichen, den Sie zuvor in der Express-Route festgelegt haben.

Mit diesem Setup können Sie JavaScript-Code vom Typ Front, Back oder Full-Stack direkt in Visual Studio Code debuggen. 

Darüber hinaus ist das Konzept des zusammengesetzten Debuggers nicht auf zwei Zielprozesse und auch nicht allein auf JavaScript beschränkt. Bei der Arbeit an einer Microservice-App (ggf. eine Polyglot-App) können Sie genau den gleichen Workflow verwenden (nachdem Sie die richtigen Erweiterungen für die Sprache bzw. das Framework installiert haben).

## <a name="dockerizing-the-app"></a>Vorbereiten der App für Docker

In diesem Abschnitt geht es um die Benutzeroberfläche, die von Visual Studio Code für die Entwicklung mit [Docker](https://www.docker.com/) bereitgestellt wird. Node.js-Entwickler nutzen Docker, um portable App-Bereitstellungen für Entwicklungs-, Continuous Integration- und Produktionsumgebungen zu ermöglichen. Da die Nutzung von Docker nicht immer einfach ist, wird in Visual Studio Code durch die Bereitstellung einer Erweiterung versucht, den Einsatz von Docker in Ihren Apps zu erleichtern.

Wechseln Sie zurück zur Registerkarte **Erweiterungen**, suchen Sie nach `docker`, und wählen Sie die Erweiterung **Docker** aus. 

Installieren Sie die Docker-Erweiterung, und laden Sie Visual Studio Code dann erneut.

![Installieren der Docker-Erweiterung für Visual Studio Code](./media/node-howto-e2e/docker-search.png)

Die Docker-Erweiterung für Visual Studio Code enthält einen Befehl zum Generieren einer *Dockerfile* und die Datei `docker-compose.yml` für ein vorhandenes Projekt. 

Zeigen Sie zum Auflisten der verfügbaren Docker-Befehle die Befehlspalette an, indem Sie **&lt;F1>** drücken und anschließend `docker` eingeben.

![Von der Docker-Erweiterung unterstützte Befehle für Visual Studio ](./media/node-howto-e2e/docker-commands.png)

Wählen Sie **Docker: Add docker files to workspace** (Docker: Docker-Dateien dem Arbeitsbereich hinzufügen), wählen Sie **Node.js** als App-Plattform aus, und geben Sie an, dass für die App der Port `8080` verfügbar gemacht wird. 

Mit dem Docker-Befehl werden eine vollständige `Dockerfile` und Docker-Compose-Dateien generiert, die Sie sofort nutzen können.

![Generierte Dockerfile](./media/node-howto-e2e/docker-file.png)

Außerdem ermöglicht die Docker-Erweiterung die automatische Vervollständigung für Ihre Dateien `Dockerfiles` und `docker-compose.yml`. 

Öffnen Sie hierzu die `Dockerfile`, und ändern Sie Zeile 2:

```docker
FROM node:latest
```

in:

```docker
FROM mhart
```

Positionieren Sie den Cursor nach dem `t` in `mhart`, und drücken Sie **&lt;STRG>+&lt;LEERTASTE>**, um alle Image-Repositorys anzuzeigen, die von `mhart` im DockerHub veröffentlicht wurden.

![Automatische Vervollständigung der Docker-Erweiterung](./media/node-howto-e2e/docker-completion.png)

Wählen Sie `mhart/alpine-node`, um alle Objekte bereitzustellen, die für diese App benötigt werden. 

Kleinere Images sind normalerweise besser geeignet, da Ihre App-Builds und -Bereitstellungen so schnell wie möglich ablaufen sollen, um die Verteilung und Skalierung zu beschleunigen.

Nachdem Sie die `Dockerfile` generiert haben, müssen Sie das eigentliche Docker-Image erstellen. Hierfür können Sie wieder einen Befehl verwenden, der von der Docker-Erweiterung in Visual Studio Code installiert wurde. Drücken Sie **&lt;F1>**, geben Sie in der Befehlspalette den Text `dockerb` ein, und wählen Sie den Befehl **Docker: Build Image** (Docker: Image erstellen). Wählen Sie die `/Dockerfile` aus, die Sie gerade generiert und geändert haben. Geben Sie ein Tag an, das Ihren DockerHub-Benutzernamen enthält (z.B. `lostintangent/node`). Drücken Sie die **&lt;EINGABETASTE>**, um das integrierte Terminalfenster zu starten, in dem die Ausgabe Ihres zu erstellenden Docker-Image angezeigt wird.

![Buildstatus des Docker-Image](./media/node-howto-e2e/docker-build.png)

Beachten Sie, dass mit dem Befehl der Prozess zur Ausführung von `docker build` für Sie automatisiert wurde. Dies ist ein weiteres Beispiel für ein Mittel zur Verbesserung der Produktivität, das Sie wählen können, oder Sie können direkt die Docker CLI nutzen. 

An diesem Punkt müssen Sie das Image nur noch per Pushvorgang an DockerHub übermitteln, damit von Bereitstellungen leicht darauf zugegriffen werden kann. Stellen Sie hierfür sicher, dass Sie die Authentifizierung mit DockerHub bereits durchgeführt haben, indem Sie `docker login` über die CLI ausführen und Ihre Anmeldeinformationen für Ihr Konto eingeben. In Visual Studio Code könne Sie dann die Befehlspalette aufrufen, `dockerpush` eingeben und den Befehl `Docker: Push` wählen. Wählen Sie das Image-Tag aus, das Sie gerade erstellt haben (z.B. `lostintangent/node`), und drücken Sie die **&lt;EINGABETASTE>**. Mit dem Befehl wird der Aufruf von `docker push` automatisiert und die Ausgabe im integrierten Terminal angezeigt.

## <a name="deploying-the-app"></a>Bereitstellen der App

Nachdem Sie die App für Docker vorbereitet und an DockerHub übermittelt haben, müssen Sie sie in der Cloud bereitstellen, damit sie öffentlich verfügbar ist. Zu diesem Zweck können Sie Azure App Service nutzen. Dies ist das PaaS-Angebot von Azure. App Service verfügt über zwei Funktionen, die für Node.js-Entwickler relevant sind:

- Unterstützung für Linux-basierte VMs: Reduziert Inkompatibilitäten für Apps, die mit nativen Node-Modulen erstellt werden, oder für andere Tools, die ggf. keine Windows-Unterstützung bzw. ein anderes Verhalten aufweisen.
- Unterstützung für Docker-basierte Bereitstellungen: Ermöglicht Ihnen das Angeben des Namens Ihres Docker-Image und für App Service das automatische „Pullen“, Bereitstellen und Skalieren des Image.

Öffnen Sie als Erstes das Visual Studio-Terminal. Sie verwenden die neue Version „Azure CLI 2.0“, um Ihr Azure-Konto zu verwalten und die erforderliche Infrastruktur zum Ausführen der To-Do-App bereitzustellen. Nachdem Sie sich über die CLI mit dem Befehl `az login` an Ihrem Konto angemeldet haben (wie in den Voraussetzungen erwähnt), können Sie die folgenden Schritte ausführen, um die App Service-Instanz und den To-Do-App-Container bereitzustellen:

1. Erstellen Sie eine Ressourcengruppe. Diese können Sie sich als *Namespace* oder *Verzeichnis* zur Unterstützung der Organisation von Azure-Ressourcen vorstellen. Die Option `-n` wird verwendet, um den Namen der Gruppe anzugeben. Dies kann ein beliebiger Name sein.

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > Mit der Option `-l` wird der Standort der Ressourcengruppe angegeben. Während der Vorschauphase ist die Unterstützung von App Service unter Linux nur in ausgewählten Regionen verfügbar. Wenn Sie nicht im Westen der USA ansässig sind und prüfen möchten, welche anderen Regionen verfügbar sind, können Sie in der CLI daher `az appservice list-locations --linux-workers-enabled` ausführen, um Ihre Optionen für Rechenzentren anzuzeigen.

2. Legen Sie die neu erstellte Ressourcengruppe als Standardressourcengruppe fest, damit Sie die CLI weiter nutzen können, ohne die Ressourcengruppe für jeden CLI-Aufruf explizit angeben zu müssen:

   ```shell
   az configure -d group=nina-demo
   ```
   
3. Erstellen Sie den App Service-*Plan*, über den die Erstellung und Skalierung der zugrunde liegenden virtuellen Computer verwaltet wird, auf denen Ihre App bereitgestellt wird. Geben Sie für die Option `n` wieder einen beliebigen Wert an.

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > Die Option „--is-linux“ gibt an, dass Sie Linux-basierte virtuelle Computer verwenden möchten. Ohne diese Option werden von der CLI standardmäßig Windows-basierte virtuelle Computer bereitgestellt.

4. Erstellen Sie die App Service-Web-App, bei der es sich um die eigentliche To-Do-App handelt, die für den eben erstellten Plan und die Ressourcengruppe ausgeführt wird. Eine Web-App ist praktisch synonym mit einem Prozess oder Container, und der Plan dient als Host für die Ausführung des virtuellen Computers bzw. Containers. Außerdem müssen Sie im Rahmen der Web-App-Erstellung die Konfiguration so durchführen, dass das von Ihnen auf DockerHub veröffentlichte Docker-Image verwendet wird:

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > Wenn Sie anstelle der Verwendung eines benutzerdefinierten Containers eine Git-Bereitstellung vorziehen, helfen Ihnen die Informationen im Artikel [Erstellen einer Node.js-Web-App in Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs) weiter.

5. Legen Sie die Web-App als Standard-Webinstanz fest:

    ```shell
    az configure -d web=nina-demo-app
    ```

6. Starten Sie die App, um den bereitgestellten Container anzuzeigen, der unter der URL vom Typ `*.azurewebsites.net` verfügbar ist:

    ```shell
    az webapp browse
    ```

    ![Ausgeführte To-Do-App im Browser](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > Der erste Ladevorgang der App kann einige Minuten dauern, da App Service das Docker-Image per Pullvorgang aus DockerHub abrufen und dann starten muss.

Sie haben die To-Do-App jetzt bereitgestellt und ausgeführt. 

Sie haben die Bereitstellung der To-Do-App jetzt abgeschlossen. Aber durch das sich drehende Symbol wird angegeben, dass die App keine Verbindung mit der Datenbank herstellen kann. Dies liegt daran, dass Sie bei der Entwicklung eine lokale Instanz von MongoDB verwendet haben, die aus den Azure-Rechenzentren natürlich nicht erreichbar ist. Da Sie die App so geändert haben, dass die Verbindungszeichenfolge über eine Umgebungsvariable akzeptiert wird, müssen Sie nur einen MongoDB-Server starten und die App Service-Instanz so konfigurieren, dass auf die Umgebungsvariable verwiesen wird. Dies wird im nächsten Abschnitt veranschaulicht.

## <a name="provisioning-a-mongodb-server"></a>Bereitstellen eines MongoDB-Servers

Sie können zwar einen MongoDB-Server oder eine Replikatgruppe konfigurieren und diese Infrastruktur selbst verwalten, aber in Azure ist hierfür eine Lösung mit dem Namen [Cosmos DB](https://azure.microsoft.com/services/documentdb/) vorhanden. Bei Cosmos DB handelt es sich um eine vollständig verwaltete NoSQL-Datenbank mit Georeplikation und hoher Leistung, über die eine MongoDB-Kompatibilitätsebene bereitgestellt wird. Dies bedeutet, dass Sie für eine vorhandene MEAN-App darauf verweisen können (oder einen beliebigen MongoDB-Client bzw. ein MongoDB-Tool, z.B. [Studio 3T](https://studio3t.com/)), ohne dass Sie außer der Verbindungszeichenfolge etwas ändern müssen. Die folgenden Schritte veranschaulichen die Vorgehensweise:

1. Führen Sie im Visual Studio Code-Terminal den folgenden Befehl aus, um eine MongoDB-kompatible Instanz des Cosmos DB-Diensts zu erstellen. Ersetzen Sie den Platzhalter **<NAME>** durch einen global eindeutigen Wert (Cosmos DB nutzt diesen Namen zum Generieren der Server-URL einer Datenbank):

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. Rufen Sie die MongoDB-Verbindungszeichenfolge für diese Instanz ab:

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. Aktualisieren Sie die Umgebungsvariable **MONGODB_URL** Ihrer Web-App so, dass eine Verbindung mit der neu bereitgestellten Cosmos DB-Instanz hergestellt und nicht versucht wird, eine Verbindung mit einem lokal ausgeführten MongoDB-Server (der nicht existiert!) herzustellen:

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. Wechseln Sie zurück in Ihren Browser, und aktualisieren Sie die Anzeige. Versuchen Sie, ein To-Do-Element hinzuzufügen und zu entfernen, um zu bestätigen, dass die App jetzt funktioniert, ohne dass etwas geändert werden muss. Legen Sie die Umgebungsvariable auf die erstellte Cosmos DB-Instanz fest, bei der es sich um eine vollständige Emulation einer MongoDB-Datenbank handelt.

    ![Demo-App nach Verbindungsherstellung mit einer Datenbank](./media/node-howto-e2e/finished-demo.png)

Bei Bedarf können Sie zurück zur Cosmos DB-Instanz wechseln und den reservierten Durchsatz, der für die MongoDB-Instanz benötigt wird, zentral hochskalieren (oder zentral herunterskalieren). So profitieren Sie von dem zusätzlichen Datenverkehr, ohne dass Sie Elemente der Infrastruktur manuell verwalten müssen.

Außerdem indiziert Cosmos DB automatisch jedes einzelne Dokument und jede Eigenschaft für Sie. Sie müssen dann keine Profile für langsame Abfragen erstellen und Ihre Indizes nicht manuell optimieren. Führen Sie die Bereitstellung und Skalierung einfach nach Bedarf durch, und überlassen Sie Cosmos DB den Rest.

## <a name="hosting-a-private-docker-registry"></a>Hosten einer privaten Docker-Registrierung

DockerHub stellt eine hervorragende Benutzeroberfläche für die Verteilung Ihrer Containerimages bereit. Es kann aber Fälle geben, in denen Sie es vorziehen, Ihre eigene private Docker-Registrierung zu hosten, z.B. im Sicherheits- oder Governance-Bereich oder zur Erzielung von Leistungsvorteilen. Für diese Zwecke enthält Azure die [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR), mit der Sie Ihre eigene Docker-Registrierung erstellen können. Der Hintergrundspeicher befindet sich hierbei in demselben Datencenter wie Ihre Web-App (ermöglicht schnellere Pullvorgänge). Mit der ACR haben Sie außerdem die volle Kontrolle über den Inhalt und die Zugriffssteuerung und können beispielsweise festlegen, welche Benutzer Push- bzw. Pullvorgänge für Images durchführen können. 

Sie können eine benutzerdefinierte Registrierung bereitstellen, indem Sie den folgenden Befehl ausführen. (Ersetzen Sie den Platzhalter **<NAME>** durch einen global eindeutigen Wert, da die ACR einen angegebenen Wert verwendet, um die Anmeldeserver-URL der Registrierung zu generieren.)

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> Im Beispiel in diesem Thema wird der Einfachheit halber das **Konto „admin“** verwendet. Für Registrierungen, die für die Produktion bestimmt sind, ist dies aber nicht zu empfehlen. 

Mit dem Befehl `az acr create` wird die Anmeldeserver-URL angezeigt (Spalte `LOGIN SERVER`), die Sie für die Anmeldung mit der Docker CLI nutzen (z.B. `ninademo.azurecr.io`). Außerdem werden mit dem Befehl Administratoranmeldeinformationen generiert, die Sie für die Authentifizierung verwenden können. Führen Sie zum Abrufen dieser Anmeldeinformationen den folgenden Befehl aus, und notieren Sie sich den angezeigten Benutzernamen und das Kennwort:

```shell
az acr credential show -n $ACR_NAME
```

Mit den Anmeldeinformationen aus dem vorherigen Schritt und Ihrem individuellen Anmeldeserver können Sie sich an der Registrierung anmelden, indem Sie den Docker CLI-Standardworkflow verwenden.

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

Sie können Ihren Docker-Container jetzt mit einem Tag versehen, um anzugeben, dass er Ihrer privaten Registrierung zugeordnet ist. Verwenden Sie hierfür den folgenden Befehl, und ersetzen Sie `lostintangent/node` durch den Namen, den Sie dem Containerimage gegeben haben.

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

Übertragen Sie das getaggte Image schließlich per Pushvorgang in Ihre private Docker-Registrierung.

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

Ihr Container ist jetzt in Ihrer eigenen privaten Registrierung gespeichert, und die Docker CLI lässt zu, dass Sie genauso wie bei der Verwendung von DockerHub weiterarbeiten. Sie müssen nur den folgenden Befehl ausführen, um die App Service-Web-App anzuweisen, den Pullvorgang aus Ihrer privaten Registrierung durchzuführen:

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> Fügen Sie am Anfang der Option `-r` das Präfix `https://` hinzu. Achten Sie aber darauf, dass Sie das Präfix nicht dem Namen des Containerimage hinzufügen.

Wenn Sie die App im Browser aktualisieren, sollte alles gleich aussehen und funktionieren. Jetzt wird Ihre App aber über Ihre private Docker-Registrierung ausgeführt. Nachdem Sie die Aktualisierung Ihrer App abgeschlossen haben, können Sie sie wie oben mit einem Tag versehen und die Änderungen per Pushvorgang übertragen und das Tag dann in Ihrer App Service-Containerkonfiguration aktualisieren.

## <a name="configuring-a-custom-domain-name"></a>Konfigurieren eines benutzerdefinierten Domänennamens

Die URL `*.azurewebsites.net` ist zwar gut für Tests geeignet, aber später kann es dann ratsam sein, Ihrer Web-App einen benutzerdefinierten Domänennamen hinzuzufügen. Nachdem Sie von einer Registrierungsstelle einen Domänennamen erhalten haben, müssen Sie ihm nur einen `A`-Eintrag hinzufügen, mit dem auf die externe IP (eigentlich ein Lastenausgleich) Ihrer Web-App verwiesen wird. Sie können diese IP abrufen, indem Sie den folgenden Befehl ausführen:

```shell
az webapp config hostname get-external-ip
```

Zusätzlich zu einem `A`-Eintrag müssen Sie Ihrer Domäne auch einen `TXT`-Eintrag hinzufügen, mit dem auf die bisher verwendete Domäne `*.azurewebsites.net` verwiesen wird. Anhand der Kombination der `A`- und `TXT`-Einträge kann Azure bestätigen, dass Sie der Besitzer der Domäne sind.

Nachdem diese Einträge erstellt – und die DNS-Änderungen weitergegeben – wurden, können Sie die benutzerdefinierte Domäne bei Azure registrieren, damit alles richtig für den eingehenden Datenverkehr vorbereitet ist. 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> Der Befehl funktioniert erst, nachdem die DNS-Änderungen weitergegeben wurden.

Öffnen Sie einen Browser, und navigieren Sie zu Ihrer benutzerdefinierten Domäne, um zu prüfen, ob nun die Auflösung zu Ihrer bereitgestellten App in Azure durchgeführt wird.

## <a name="scaling-up-and-out"></a>Zentrales Hochskalieren und horizontales Hochskalieren

Unter Umständen erreicht Ihre Web-App nach einiger Zeit eine so große Beliebtheit, dass ihre zugeordneten Ressourcen (CPU und RAM) nicht mehr ausreichen, um den vermehrten Datenverkehr und die Betriebsanforderungen zu bewältigen. Der App Service-Plan, den Sie weiter oben erstellt haben (**B1**), verfügt über einen CPU-Kern und 1,75 GB RAM. Damit ist die Auslastungsgrenze relativ schnell erreicht. Der Plan **B2** verfügt über doppelt so hohe RAM- und CPU-Werte. Wenn Sie merken, dass einer der Werte für Ihre App nicht mehr ausreicht, können Sie den zugrunde liegenden virtuellen Computer also zentral hochskalieren, indem Sie den folgenden Befehl ausführen:

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> Preisangaben und Spezifikationen für Azure-App-Pläne finden Sie im Artikel [App Service – Preise](https://azure.microsoft.com/pricing/details/app-service/).

Nach kurzer Zeit wird Ihre Web-App zu der angeforderten Hardware migriert, und die zugeordneten Ressourcen können genutzt werden. Sie können nicht nur zentral hochskalieren, sondern auch zentral herunterskalieren, indem Sie den gleichen Befehl wie oben ausführen. Geben Sie hierbei aber die Option `--sku` an, damit weniger Ressourcen zu einem geringeren Preis bereitgestellt werden. 

Zusätzlich zum zentralen Hochskalieren der Spezifikationen für den virtuellen Computer können Sie Ihre Web-App auch *horizontal hochskalieren* (sofern die Web-App zustandslos ist), indem Sie weitere zugrunde liegende VM-Instanzen hinzufügen. Der weiter oben erstellte App Service-Plan enthält nur einen virtuellen Computer (einen *Worker*). Daher wird der gesamte eingehende Datenverkehr letztendlich durch die Grenzwerte der verfügbaren Ressourcen dieser einen Instanz begrenzt. Wenn Sie eine zweite VM-Instanz hinzufügen möchten, können Sie den gleichen Befehl wie oben ausführen und nun anstelle der SKU die Anzahl von virtuellen Workercomputern horizontal hochskalieren.

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

Wenn Sie eine Web-App auf diese Weise horizontal hochskalieren, wird für den eingehenden Datenverkehr auf transparente Weise für alle Instanzen ein Lastenausgleich durchgeführt. So können Sie Ihre Kapazität sofort erhöhen, ohne dass Sie Code ändern oder sich Gedanken zur erforderlichen Infrastruktur machen müssen. 

Die Verwendung von zustandslosen Web-Apps wird als bewährte Methode angesehen. Sie machen die Möglichkeit zum Skalieren (zentral hoch, zentral herunter, horizontal hoch) vollständig deterministisch, da kein einzelner virtueller Computer oder eine App-Instanz einen Zustand aufweist, der für den korrekten Betrieb erforderlich ist. 

> [!NOTE]
> Im Tutorial dieses Themas wird die Ausführung einer einzelnen Web-App im Rahmen eines App Service-Plans veranschaulicht. Sie können aber mehrere Web-Apps unter demselben Plan erstellen und bereitstellen, sodass Sie bei Bedarf auch einen einzelnen Plan bereitstellen können und dann nur dafür zahlen müssen. 

## <a name="clean-up"></a>Bereinigung

Um sicherzustellen, dass Ihnen für nicht genutzte Azure-Ressourcen keine Kosten berechnet werden, können Sie im Visual Studio Code-Terminal den folgenden Befehl ausführen. Mit dem Befehl werden alle Ressourcen gelöscht, die während dieses Tutorials bereitgestellt wurden.

```shell
az group delete
```

> [!NOTE]
> Es kann einige Minuten dauern, bis der Bereinigungsvorgang abgeschlossen ist. 

Nach Abschluss des Vorgangs befindet sich Ihr Azure-Konto mit dem Befehl `az group delete` in dem gleichen Zustand wie vor Beginn des Tutorials. Die Möglichkeit, Azure-Ressourcen als einzelne Einheit zu organisieren, bereitzustellen und zu löschen, ist einer der Hauptvorteile von Ressourcengruppen. Daher wird empfohlen, Ressourcen zu gruppieren, für die Sie die gleiche Lebensdauer erwarten.