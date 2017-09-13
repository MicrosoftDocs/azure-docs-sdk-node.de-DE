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
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a><span data-ttu-id="25181-103">Node.js-Entwicklung mit Visual Studio Code und Azure</span><span class="sxs-lookup"><span data-stu-id="25181-103">Node.js development with Visual Studio Code and Azure</span></span>

<span data-ttu-id="25181-104">In diesem Tutorial wird veranschaulicht, wie Sie eine vorhandene Node.js-App (mit Docker) in einem Container anordnen und die App anschließend mit Visual Studio Code in Azure bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="25181-104">This tutorial illustrates taking an existing Node.js app, "containerizing" it (with Docker), and then deploying the app to Azure using Visual Studio Code.</span></span>

<span data-ttu-id="25181-105">Für das Tutorial wird eine einfache To-Do-App genutzt, die von [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular) erstellt und veröffentlicht wurde.</span><span class="sxs-lookup"><span data-stu-id="25181-105">The tutorial makes use of a simple todo app created by and published by [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular).</span></span> <span data-ttu-id="25181-106">Da es sich hierbei um eine einseitige MEAN-App handelt, wird MongoDB als Datenbank, Node/Express für die REST-API bzw. den Webserver und Angular.js 1.x für die Front-End-Benutzeroberfläche verwendet.</span><span class="sxs-lookup"><span data-stu-id="25181-106">It is a single-page MEAN app, and therefore, uses MongoDB as its database, Node/Express for the REST API/web server, and Angular.js 1.x for the front-end UI.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="25181-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="25181-107">Prerequisites</span></span>

<span data-ttu-id="25181-108">Zum Durcharbeiten der Demo muss die folgende Software installiert sein:</span><span class="sxs-lookup"><span data-stu-id="25181-108">In order to follow along with the demo, you'll need to have the following software installed:</span></span>

- [<span data-ttu-id="25181-109">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="25181-109">Visual Studio Code</span></span>](https://code.visualstudio.com/)
- [<span data-ttu-id="25181-110">Docker</span><span class="sxs-lookup"><span data-stu-id="25181-110">Docker</span></span>](https://www.docker.com/products/docker)
- [<span data-ttu-id="25181-111">DockerHub-Konto</span><span class="sxs-lookup"><span data-stu-id="25181-111">DockerHub account</span></span>](https://hub.docker.com/)
- [<span data-ttu-id="25181-112">Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="25181-112">Azure CLI 2.0</span></span>](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [<span data-ttu-id="25181-113">Azure-Konto</span><span class="sxs-lookup"><span data-stu-id="25181-113">Azure account</span></span>](https://azure.microsoft.com/free/)
- [<span data-ttu-id="25181-114">YARN</span><span class="sxs-lookup"><span data-stu-id="25181-114">Yarn</span></span>](https://yarnpkg.com/en/docs/install)
- <span data-ttu-id="25181-115">[Chrome](https://www.google.com/chrome/browser/desktop/): Wird verwendet, um das Front-End der Demo-App zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="25181-115">[Chrome](https://www.google.com/chrome/browser/desktop/) - Used for debugging the demo app's front-end.</span></span>
- <span data-ttu-id="25181-116">MongoDB: Da für die Demo-App MongoDB verwendet wird, müssen Sie über eine lokal ausgeführte MongoDB-Instanz verfügen, die über den Standardport `27017` lauscht.</span><span class="sxs-lookup"><span data-stu-id="25181-116">MongoDB - Since the demo app uses MongoDB, you need to have a locally running MongoDB instance that is listening on the standard `27017` port.</span></span> <span data-ttu-id="25181-117">Dies lässt sich am einfachsten erreichen, indem nach der Installation von Docker die folgenden beiden Befehle ausgeführt werden: `docker pull mongo` gefolgt von `docker run -it -p 27017:27017 mongo`.</span><span class="sxs-lookup"><span data-stu-id="25181-117">The simplest way to achieve this is by running the following two commands after Docker is installed: `docker pull mongo` followed by `docker run -it -p 27017:27017 mongo`.</span></span>

## <a name="project-setup"></a><span data-ttu-id="25181-118">Projekteinrichtung</span><span class="sxs-lookup"><span data-stu-id="25181-118">Project setup</span></span>

<span data-ttu-id="25181-119">Laden Sie als Erstes das Beispielprojekt herunter, indem Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="25181-119">To get started, download the sample project using the following steps:</span></span>

1. <span data-ttu-id="25181-120">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="25181-120">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="25181-121">Drücken Sie **&lt;F1>**, um die Befehlspalette anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="25181-121">Press **&lt;F1>** to display the command palette.</span></span>

1. <span data-ttu-id="25181-122">Geben Sie an der Eingabeaufforderung der Befehlspalette `gitcl` ein, wählen Sie den Befehl **Git: Clone** aus, und drücken Sie die **&lt;EINGABETASTE>**.</span><span class="sxs-lookup"><span data-stu-id="25181-122">At the command palette prompt, enter `gitcl`, select the **Git: Clone** command, and press **&lt;Enter>**.</span></span>

    ![Befehl „gitcl“ in der Eingabeaufforderung der Befehlspalette von Visual Studio Code](./media/node-howto-e2e/git-clone.png)

1. <span data-ttu-id="25181-124">Geben Sie `https://github.com/scotch-io/node-todo` ein, wenn Sie zum Eingeben der **Repository-URL** aufgefordert werden, und drücken Sie anschließend die **&lt;EINGABETASTE>**.</span><span class="sxs-lookup"><span data-stu-id="25181-124">When prompted for the **Repository URL**, enter `https://github.com/scotch-io/node-todo`, then press **&lt;Enter>**.</span></span>

1. <span data-ttu-id="25181-125">Wählen bzw. erstellen Sie das lokale Verzeichnis, in dem das Projekt geklont werden soll.</span><span class="sxs-lookup"><span data-stu-id="25181-125">Select (or create) the local directory into which you want to clone the project.</span></span>

    ![Visual Studio Code-Explorer](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a><span data-ttu-id="25181-127">Integriertes Terminal</span><span class="sxs-lookup"><span data-stu-id="25181-127">Integrated terminal</span></span>

<span data-ttu-id="25181-128">Da es sich um ein Node.js-Projekt handelt, müssen Sie zunächst sicherstellen, dass alle Abhängigkeiten des Projekts über npm installiert wurden.</span><span class="sxs-lookup"><span data-stu-id="25181-128">Since this is a Node.js project, the first thing you need to do is ensure that all of the project's dependencies are installed from npm.</span></span>  

1. <span data-ttu-id="25181-129">Drücken Sie **&lt;STRG>+'** (bzw. die entsprechende Tastenkombination für das deutsche Tastaturlayout), um das integrierte Terminal von Visual Studio Code anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="25181-129">Press **&lt;Ctrl>\`** to display the Visual Studio Code integrated terminal.</span></span> 

1. <span data-ttu-id="25181-130">Geben Sie `yarn` ein, und drücken Sie die **&lt;EINGABETASTE>**.</span><span class="sxs-lookup"><span data-stu-id="25181-130">Enter `yarn`, and press **&lt;Enter>**.</span></span>  

    ![Ausführen des Befehls „yarn“ in Visual Studio Code](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a><span data-ttu-id="25181-132">Integrierte Git-Versionskontrolle</span><span class="sxs-lookup"><span data-stu-id="25181-132">Integrated Git version control</span></span>

<span data-ttu-id="25181-133">Nach der Installation der App-Abhängigkeiten per YARN wird die Datei `yarn.lock` erstellt, um auf einfache Weise dafür zu sorgen, dass später die gleichen Abhängigkeiten beschafft werden können. So wird ausgeschlossen, dass es in Bezug auf Continuous Integration-Builds, Produktionsbereitstellungen oder andere Entwicklercomputer zu Überraschungen kommt.</span><span class="sxs-lookup"><span data-stu-id="25181-133">After installing the app's dependencies via Yarn, a `yarn.lock` file is created that provides a predictable way to reacquire the exact same dependencies in the future, without any surprises in either CI (continuous integration) builds, production deployments, or other developer machines.</span></span>

<span data-ttu-id="25181-134">In den folgenden Schritten wird veranschaulicht, wie Sie die Datei `yarn.lock` in die Quellcodeverwaltung einchecken:</span><span class="sxs-lookup"><span data-stu-id="25181-134">The following steps illustrate how to check the `yarn.lock` file into source control:</span></span>

1. <span data-ttu-id="25181-135">Wechseln Sie in Visual Studio Code zur integrierten Git-Registerkarte (die Registerkarte mit dem Git-Logo).</span><span class="sxs-lookup"><span data-stu-id="25181-135">Within Visual Studio Code, switch to the integrated Git tab (the tab with the Git logo).</span></span>

1. <span data-ttu-id="25181-136">Geben Sie im Feld **Nachricht** eine Commit-Nachricht ein, und drücken Sie **&lt;STRG>+&lt;EINGABETASTE>**.</span><span class="sxs-lookup"><span data-stu-id="25181-136">In the **Message** box, enter a commit message, and press **&lt;Ctrl>&lt;Enter>**.</span></span> 

    ![Hinzufügen der Datei „yarn.lock“ zu Git](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a><span data-ttu-id="25181-138">Projekt- und Codenavigation</span><span class="sxs-lookup"><span data-stu-id="25181-138">Project and code navigation</span></span>

<span data-ttu-id="25181-139">Zur besseren Orientierung in der Codebase probieren wir nun einige Beispiele für die Navigationsfunktionen von Visual Studio Code aus.</span><span class="sxs-lookup"><span data-stu-id="25181-139">In order to orient ourselves within the codebase, let's play around with some examples of some of the navigation capabilities that Visual Studio Code provides.</span></span>

1. <span data-ttu-id="25181-140">Drücken Sie **&lt;STRG>+P**.</span><span class="sxs-lookup"><span data-stu-id="25181-140">Press **&lt;Ctrl>P**.</span></span>

1. <span data-ttu-id="25181-141">Geben Sie `.js` ein, um alle JavaScript/JSON-Dateien des Projekts mit dem jeweiligen übergeordneten Verzeichnis anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="25181-141">Enter `.js` to display all the JavaScript/JSON files in the project along with each file's parent directory</span></span> 

    ![Anzeigen aller JS-Dateien](./media/node-howto-e2e/git-output.png)

1. <span data-ttu-id="25181-143">Wählen Sie `server.js` aus. Dies ist das Startskript für die App.</span><span class="sxs-lookup"><span data-stu-id="25181-143">Select `server.js`, which is the startup script for the app.</span></span> 

1. <span data-ttu-id="25181-144">Bewegen Sie den Mauszeiger auf die Variable **database** (in Zeile 6 importiert), um ihren Typ anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="25181-144">Hover your mouse over the **database** variable (imported on line 6) to see its type.</span></span> <span data-ttu-id="25181-145">Diese Möglichkeit zum schnellen Prüfen von Variablen, Modulen und Typen in einer Datei ist bei der Entwicklung Ihrer Projekte sehr hilfreich.</span><span class="sxs-lookup"><span data-stu-id="25181-145">This ability to quickly inspect variables/modules/types within a file is very useful during the development of your projects.</span></span> 

    ![Ermitteln des Typs](./media/node-howto-e2e/hover-help.png)

1. <span data-ttu-id="25181-147">Wenn Sie mit der Maus in den Bereich einer Variablen – z.B. **database** – klicken, können Sie alle Verweise auf diese Variable anzeigen, die in der Datei enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="25181-147">Clicking your mouse within the span of a variable - such as **database** - allows you to see all references to that variable within the same file.</span></span> <span data-ttu-id="25181-148">Um alle Verweise auf eine Variable für das gesamte Projekt anzuzeigen, klicken Sie mit der rechten Maustaste auf die Variable und wählen im Kontextmenü die Option **Alle Verweise suchen**.</span><span class="sxs-lookup"><span data-stu-id="25181-148">To view all references to a variable within the project, right-click the variable, and from the context menu, and select **Find All References**.</span></span>

    ![Suchen nach den Verweisen auf eine Variable](./media/node-howto-e2e/word-hilight.png)

1. <span data-ttu-id="25181-150">Zusätzlich zum Zeigen auf eine Variable mit der Maus, um ihren Typ zu ermitteln, können Sie auch die Definition einer Variablen untersuchen. Dies ist sogar möglich, wenn sie sich in einer anderen Datei befindet.</span><span class="sxs-lookup"><span data-stu-id="25181-150">In addition to being to hover your mouse over a variable to discover its type, you can also inspect the definition of a variable, even if it's in another file.</span></span> <span data-ttu-id="25181-151">Klicken Sie hierzu mit der rechten Maustaste auf **database.localUrl** (Zeile 12), und wählen Sie im Kontextmenü die Option **Definition einsehen**.</span><span class="sxs-lookup"><span data-stu-id="25181-151">To see this in action, right-click **database.localUrl** (line 12), and, from the context menu, select **Peek Definition**.</span></span> 

    ![Einsehen der Definition einer Variablen](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a><span data-ttu-id="25181-153">Ändern des Codes und Verwenden der automatischen Vervollständigung</span><span class="sxs-lookup"><span data-stu-id="25181-153">Modifying the code and using autocompletion</span></span>

<span data-ttu-id="25181-154">Die MongoDB-Verbindungszeichenfolge ist in der Deklaration von **database.localUrl** hartcodiert.</span><span class="sxs-lookup"><span data-stu-id="25181-154">The MongoDB connection string is hard-coded in declaration of the **database.localUrl**.</span></span> <span data-ttu-id="25181-155">In diesem Abschnitt ändern Sie den Code, um die Verbindungszeichenfolge aus einer Umgebungsvariablen abzurufen, und machen sich mit dem AutoVervollständigen-Feature von Visual Studio Code vertraut.</span><span class="sxs-lookup"><span data-stu-id="25181-155">In this section, you'll modify the code to retrieve the connection string from an environment variable, and learn about Visual Studio Code's autocompetion feature.</span></span>  

1. <span data-ttu-id="25181-156">Öffnen Sie die Datei `server.js`.</span><span class="sxs-lookup"><span data-stu-id="25181-156">Open the `server.js` file</span></span>

1. <span data-ttu-id="25181-157">Ersetzen Sie den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="25181-157">Replace the following code:</span></span> 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    <span data-ttu-id="25181-158">durch diesen Code:</span><span class="sxs-lookup"><span data-stu-id="25181-158">with this code:</span></span>

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

<span data-ttu-id="25181-159">Beachten Sie Folgendes: Bei der manuellen Eingabe des Codes (anstelle von Kopieren und Einfügen) werden in Visual Studio Code die verfügbaren Elemente für die globale API des Node.js-**Prozesses** angezeigt, wenn Sie nach `process` den Punkt eingeben.</span><span class="sxs-lookup"><span data-stu-id="25181-159">Note that if you type the code in manually (instead of copy and paste), when you type the period after `process`, Visual Studio Code displays the available members of the Node.js **process** global API.</span></span>

![Automatische Anzeige der API-Elemente bei AutoVervollständigen](./media/node-howto-e2e/process-env.png)

<span data-ttu-id="25181-161">AutoVervollständigen funktioniert, weil von Visual Studio Code im Hintergrund TypeScript verwendet wird (auch für JavaScript). So werden Typinformationen angegeben, die dann während der Eingabe für die Vervollständigungsliste genutzt werden können.</span><span class="sxs-lookup"><span data-stu-id="25181-161">Autocompetion works because Visual Studio Code uses TypeScript behind the scenes - even for JavaScript - to provide type information that can then be used to inform the completion list as you type.</span></span> <span data-ttu-id="25181-162">Visual Studio Code erkennt, dass es sich um ein Node.js-Projekt handelt, und die TypeScript-Typisierungsdatei für [Node.js wird automatisch von NPM heruntergeladen](https://www.npmjs.com/package/@types/node).</span><span class="sxs-lookup"><span data-stu-id="25181-162">Visual Studio Code is able to detect that this is a Node.js project, and as a result, automatically downloaded the TypeScript typings file for [Node.js from NPM](https://www.npmjs.com/package/@types/node).</span></span> <span data-ttu-id="25181-163">Mit der Typisierungsdatei können Sie die automatische Vervollständigung auch für andere globale Node.js-Elemente, z.B. **Buffer** und **setTimeout**, sowie alle integrierten Module, z.B. **fs** und **http**, nutzen.</span><span class="sxs-lookup"><span data-stu-id="25181-163">The typings file allows you to get autocompletion for other Node.js globals - such as **Buffer** and **setTimeout** - as well as all of the built-in modules such as **fs** and **http**.</span></span>

<span data-ttu-id="25181-164">Diese automatische Beschaffung von Typisierungen funktioniert nicht nur für die integrierten Node.js-APIs, sondern auch für mehr als 2.000 Drittanbietermodule, z.B. React, Underscore und Express.</span><span class="sxs-lookup"><span data-stu-id="25181-164">In addition to the built-in Node.js APIs, this auto-acquisition of typings also works for over 2,000 3rd party modules, such as React, Underscore and Express.</span></span> <span data-ttu-id="25181-165">Um beispielsweise zu verhindern, dass die Beispiel-App für Mongoose abstürzt, wenn keine Verbindung mit der konfigurierten MongoDB-Datenbankinstanz hergestellt werden kann, können Sie in Zeile 13 die folgende Codezeile einfügen:</span><span class="sxs-lookup"><span data-stu-id="25181-165">For example, in order to disable Mongoose from crashing the sample app if it can't connect to the configured MongoDB database instance, insert the following line of code at  line 13:</span></span>

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

<span data-ttu-id="25181-166">Wie beim vorherigen Code auch, erhalten Sie die automatische Vervollständigung ohne jegliches Zutun.</span><span class="sxs-lookup"><span data-stu-id="25181-166">As with the previous code, you'll notice that you get autocompletion without any work on your part.</span></span>

![Automatische Anzeige der API-Elemente bei AutoVervollständigen](./media/node-howto-e2e/mongoose.png)

<span data-ttu-id="25181-168">Sie können anzeigen, welche Module die automatische Vervollständigung unterstützen, indem Sie das Projekt [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) durchsuchen. Dies ist die von der Community gestützte Quelle aller TypeScript-Typdefinitionen.</span><span class="sxs-lookup"><span data-stu-id="25181-168">You can see which modules support this auto-complete capability by browsing the [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) project, which is the community-driven source of all TypeScript type definitions.</span></span>

## <a name="running-the-app"></a><span data-ttu-id="25181-169">Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="25181-169">Running the app</span></span>

<span data-ttu-id="25181-170">Nachdem Sie den Code untersucht haben, können Sie die App ausführen.</span><span class="sxs-lookup"><span data-stu-id="25181-170">Once you've explored the code a bit, it's time to run the app.</span></span> <span data-ttu-id="25181-171">Drücken Sie **&lt;F5>**, um die App über Visual Studio Code auszuführen.</span><span class="sxs-lookup"><span data-stu-id="25181-171">To run the app from Visual Studio Code, press **&lt;F5>**.</span></span> <span data-ttu-id="25181-172">Beim Ausführen des Codes mit **&lt;F5>** (Debugmodus) startet Visual Studio Code die App und öffnet das Fenster **Debugging-Konsole**, in dem die StdOut-Daten für die App angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="25181-172">When running the code via **&lt;F5>** (debug mode), Visual Studio Code launches the app and displays the **Debug Console** window that displays stdout for the app.</span></span>

![Überwachen der StdOut-Daten einer App über die Debugging-Konsole](./media/node-howto-e2e/console.png)

<span data-ttu-id="25181-174">Die **Debugging-Konsole** wird auch an die neu ausgeführte App angefügt, sodass Sie JavaScript-Ausdrücke eingeben können, die in der App ausgewertet werden. Außerdem ist die automatische Vervollständigung verfügbar.</span><span class="sxs-lookup"><span data-stu-id="25181-174">Additionally, the **Debug Console** is attached to the newly running app so you can type JavaScript expressions, which will be evaluated in the app, and also includes auto-completion.</span></span> <span data-ttu-id="25181-175">Geben Sie in der Konsole `process.env` ein, um dies in Aktion zu sehen:</span><span class="sxs-lookup"><span data-stu-id="25181-175">To see this in action, type `process.env` in the console:</span></span>

![Eingeben von Code in der Debugging-Konsole](./media/node-howto-e2e/console-code.png)

<span data-ttu-id="25181-177">Das Drücken von **&lt;F5>** zum Ausführen der App war möglich, da die derzeit geöffnete Datei eine JavaScript-Datei ist (`server.js`).</span><span class="sxs-lookup"><span data-stu-id="25181-177">You were able to press **&lt;F5>** to run the app because the currently open file is a JavaScript file (`server.js`).</span></span> <span data-ttu-id="25181-178">Visual Studio Code nimmt daher an, dass es sich bei dem Projekt um eine Node.js-App handelt.</span><span class="sxs-lookup"><span data-stu-id="25181-178">As a result, Visual Studio Code assumes that the project is a Node.js app.</span></span> <span data-ttu-id="25181-179">Wenn Sie alle JavaScript-Dateien in Visual Studio Code schließen und dann **&lt;F5>** drücken, fragt Visual Studio Code die Umgebung ab:</span><span class="sxs-lookup"><span data-stu-id="25181-179">If you close all JavaScript files in Visual Studio Code, and then press **&lt;F5>**, Visual Studio Code will query you as the environment:</span></span>

![Angeben der Laufzeitumgebung](./media/node-howto-e2e/select-env.png)

<span data-ttu-id="25181-181">Öffnen Sie einen Browser, und navigieren Sie zu `http://localhost:8080`, um die ausgeführte App anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="25181-181">Open a browser, and navigate to `http://localhost:8080` to see the running app.</span></span> <span data-ttu-id="25181-182">Geben Sie eine Nachricht in das Textfeld ein, und fügen Sie einige Aufgaben hinzu (bzw. entfernen Sie sie), um ein Gefühl für die Funktionsweise der App zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="25181-182">Type a message into the textbox and add/remove a few todos to get a feel for how the app works.</span></span>

![Ausgeführte To-Do-App](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a><span data-ttu-id="25181-184">Debuggen</span><span class="sxs-lookup"><span data-stu-id="25181-184">Debugging</span></span>

<span data-ttu-id="25181-185">In Visual Studio Code können Sie nicht nur die App ausführen und über die integrierte Konsole damit interagieren, sondern auch direkt im Code Breakpoints festlegen.</span><span class="sxs-lookup"><span data-stu-id="25181-185">In addition to being able to run the app and interact with it via the integrated console, Visual Studio Code provides the ability to set breakpoints directly within your code.</span></span> <span data-ttu-id="25181-186">Drücken Sie beispielsweise **&lt;STRG>+P**, um die Dateiauswahl anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="25181-186">For example, press **&lt;Ctrl>P** to display the file picker.</span></span> <span data-ttu-id="25181-187">Geben Sie in der Dateiauswahl `route` ein, und wählen Sie die Datei `route.js`.</span><span class="sxs-lookup"><span data-stu-id="25181-187">Once the file picker displays, type `route`, and select the `route.js` file.</span></span>

<span data-ttu-id="25181-188">Legen Sie in Zeile 28 einen Breakpoint fest. Dieser Breakpoint steht für die Express-Route, die aufgerufen wird, wenn die App versucht, einen To-Do-Eintrag hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="25181-188">Set a breakpoint on line 28, which represents the Express route that is called when the app tries to add a todo entry.</span></span> <span data-ttu-id="25181-189">Klicken Sie zum Festlegen eines Breakpoints im Editor einfach auf den Bereich links von der Zeilennummer. Dies ist in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="25181-189">To set a breakpoint, simply click the area to the left of the line number within the editor as shown in the following figure.</span></span>

![Festlegen eines Breakpoints in Visual Studio Code](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> <span data-ttu-id="25181-191">Neben Standard-Breakpoints unterstützt Visual Studio Code auch bedingte Breakpoints, mit denen Sie anpassen können, wann die Ausführung der App angehalten werden soll.</span><span class="sxs-lookup"><span data-stu-id="25181-191">In addition to standard breakpoints, Visual Studio Code supports conditional breakpoints that allow you to customize when the app should suspend execution.</span></span> <span data-ttu-id="25181-192">Klicken Sie zum Festlegen eines bedingten Breakpoints mit der rechten Maustaste auf den Bereich links von der Zeile, in der Sie die Ausführung anhalten möchten. Wählen Sie dann **Bedingten Haltepunkt hinzufügen...**, und geben Sie entweder einen JavaScript-Ausdruck (z.B. `foo = "bar"`) oder eine Ausführungsanzahl an, um die Bedingung zu definieren, unter der die Ausführung angehalten werden soll.</span><span class="sxs-lookup"><span data-stu-id="25181-192">To set a conditional breakpoint, right-click the area to the left of the line on which you wish to pause execution, select **Add Conditional Breakpoint...**, and specify either a JavaScript expression (e.g. `foo = "bar"`) or execution count that defines the condition under which you want to pause execution.</span></span>
> 
> 

<span data-ttu-id="25181-193">Wechseln Sie nach dem Festlegen des Breakpoints zurück zur ausgeführten App, und fügen Sie einen To-Do-Eintrag hinzu.</span><span class="sxs-lookup"><span data-stu-id="25181-193">Once the breakpoint has been set, return to the running app and add a todo entry.</span></span> <span data-ttu-id="25181-194">Das Hinzufügen eines To-Do-Eintrags bewirkt sofort, dass die Ausführung der App in Zeile 28 angehalten wird, in der Sie den Breakpoint festgelegt haben:</span><span class="sxs-lookup"><span data-stu-id="25181-194">Adding a todo entry immediately causes the app to suspend execution on line 28 where you set the breakpoint:</span></span>

![Unterbrechung der Visual Studio Code-Ausführung an einem Breakpoint](./media/node-howto-e2e/debugger.png)

<span data-ttu-id="25181-196">Nachdem die Anwendung angehalten wurde, können Sie den Mauszeiger auf die Ausdrücke des Codes bewegen, um ihren aktuellen Wert anzuzeigen, die lokalen Elemente bzw. Überwachungselemente und die Aufrufliste untersuchen und die Debug-Symbolleiste für den Schritt-für-Schritt-Durchlauf durch die Codeausführung verwenden.</span><span class="sxs-lookup"><span data-stu-id="25181-196">Once the application has been paused, you can hover your mouse over the code's expressions to view their current value, inspect the locals/watches and call stack, and use the debug toolbar to step through the code execution.</span></span> <span data-ttu-id="25181-197">Drücken Sie **&lt;F5>**, um die Ausführung der App fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="25181-197">Press **&lt;F5>** to resume execution of the app.</span></span>

## <a name="full-stack-debugging"></a><span data-ttu-id="25181-198">Full-Stack-Debuggen</span><span class="sxs-lookup"><span data-stu-id="25181-198">Full-stack debugging</span></span>

<span data-ttu-id="25181-199">Wie in diesem Thema bereits erwähnt wurde, ist die To-Do-App eine MEAN-App. Dies bedeutet, dass sowohl ihr Front-End als auch ihr Back-End mit JavaScript geschrieben wurden.</span><span class="sxs-lookup"><span data-stu-id="25181-199">As mentioned earlier in the topic, the TODO app is a MEAN app - meaning that its front-end and back-end are both written using JavaScript.</span></span> <span data-ttu-id="25181-200">Derzeit debuggen Sie den Back-End-Code (Node/Express), aber es kann sein, dass Sie später auch den Front-End-Code (Angular) debuggen müssen.</span><span class="sxs-lookup"><span data-stu-id="25181-200">So, while you're currently debugging the back-end (Node/Express) code, at some point, you may need to debug the front-end (Angular) code.</span></span> <span data-ttu-id="25181-201">Hierfür verfügt Visual Studio Code über ein umfangreiches Ökosystem mit Erweiterungen, z.B. integriertes Chrome-Debugging.</span><span class="sxs-lookup"><span data-stu-id="25181-201">For that purpose, Visual Studio Code has a huge ecosystem of extensions, including integrated Chrome debugging.</span></span>

<span data-ttu-id="25181-202">Wechseln Sie zur Registerkarte **Erweiterungen**, und geben Sie im Suchfeld `chrome` ein:</span><span class="sxs-lookup"><span data-stu-id="25181-202">Switch to the **Extensions** tab, and type `chrome` into the search box:</span></span>

![Erweiterung zum Debuggen von Chrome in Visual Studio Code](./media/node-howto-e2e/chrome.png)

<span data-ttu-id="25181-204">Wählen Sie die Erweiterung mit dem Namen **Debugger for Chrome** aus, und wählen Sie anschließend die Option **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="25181-204">Select the extension named **Debugger for Chrome**, and select **Install**.</span></span> <span data-ttu-id="25181-205">Wählen Sie nach der Installation der Erweiterung für das Chrome-Debugging die Option **Erneut laden**, um Visual Studio Code zu schließen und wieder zu öffnen und die Erweiterung so zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="25181-205">After installing the Chrome debugging extension, select **Reload** to close and reopen Visual Studio Code in order to activate the extension.</span></span> 

![Erneutes Laden von Visual Studio Code nach der Erweiterung für das Chrome-Debugging](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

<span data-ttu-id="25181-207">Sie konnten den Node.js-Code ohne jegliche Visual Studio Code-spezifische Konfiguration ausführen und debuggen. Zum Debuggen einer Front-End-Web-App müssen Sie die Datei `launch.json` generieren, in der Visual Studio Code angewiesen wird, wie die App ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="25181-207">While you were able to run and debug the Node.js code without any Visual Stdio Code-specific configuration, in order to debug a front-end web app, you need to generate a `launch.json` file that instructs Visual Studio Code how to run the app.</span></span> 

<span data-ttu-id="25181-208">Wechseln Sie zum Generieren der Datei `launch.json` zur Registerkarte **Debuggen**, klicken Sie auf das Zahnradsymbol (das mit einem kleinen roten Punkt versehen sein sollte), und wählen Sie die Umgebung **node.js** aus.</span><span class="sxs-lookup"><span data-stu-id="25181-208">To generate the `launch.json` file, switch to the **Debug** tab, click the gear icon (which should have a little red dot on top of it), and select the **node.js** environment.</span></span>

![Visual Studio Code-Option zum Konfigurieren der Datei „launch.json“](./media/node-howto-e2e/debug-gear.png)

<span data-ttu-id="25181-210">Nach der Erstellung sieht die Datei `launch.json` etwa wie unten angegeben aus. Hiermit wird Visual Studio Code mitgeteilt, wie die App gestartet bzw. wie das Anfügen für das Debuggen durchgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="25181-210">Once created, the `launch.json` file looks similar to the following, and tells Visual Studio Code how to launch and/or attach to the app in order to debug it.</span></span> 

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

<span data-ttu-id="25181-211">Beachten Sie Folgendes: Visual Studio Code hat erkannt, dass `server.js` das Startskript der App ist.</span><span class="sxs-lookup"><span data-stu-id="25181-211">Note that Visual Studio Code was able to detect that the app's startup script is `server.js`.</span></span> 

<span data-ttu-id="25181-212">Wählen Sie bei geöffneter Datei `launch.json` die Option **Konfiguration hinzufügen** (unten rechts) und anschließend die Option **Chrome: Launch with userDataDir** (Chrome: Mit userDataDir starten).</span><span class="sxs-lookup"><span data-stu-id="25181-212">With the `launch.json` file open, select **Add Configuration** (bottom right), and select **Chrome: Launch with userDataDir**.</span></span>

![Hinzufügen einer Chrome-Konfiguration zu Visual Studio Code](./media/node-howto-e2e/add-chrome-config.png)

<span data-ttu-id="25181-214">Wenn Sie eine neue Laufzeitkonfiguration für Chrome hinzufügen, können Sie den JavaScript-Code des Front-Ends debuggen.</span><span class="sxs-lookup"><span data-stu-id="25181-214">Adding a new run configuration for Chrome allows you to debug the front-end JavaScript code.</span></span> 

<span data-ttu-id="25181-215">Sie können den Mauszeiger auf alle angegebenen Einstellungen bewegen, um Dokumentation zum Zweck der Einstellung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="25181-215">You can hover your mouse over any of the settings that are specified to view documentation about what the setting does.</span></span> <span data-ttu-id="25181-216">Beachten Sie auch, dass Visual Studio Code die URL der App automatisch erkennt.</span><span class="sxs-lookup"><span data-stu-id="25181-216">Additionally, notice that Visual Studio Code automatically detects the URL of the app.</span></span> <span data-ttu-id="25181-217">Aktualisieren Sie die **webRoot**-Eigenschaft in `${workspaceRoot}/public`, damit der Chrome-Debugger weiß, wo sich die Front-End-Objekte der App befinden:</span><span class="sxs-lookup"><span data-stu-id="25181-217">Update the **webRoot** property to `${workspaceRoot}/public` so that the Chrome debugger will know where to find the app's front-end assets:</span></span>

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

<span data-ttu-id="25181-218">Um das Front-End und Back-End gleichzeitig zu starten oder zu debuggen, müssen Sie eine zusammengesetzte Laufzeitkonfiguration (*compound*) erstellen, damit Visual Studio Code weiß, welche Konfigurationssätze parallel ausgeführt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="25181-218">In order to launch/debug both the front and back-end at the same time, you need to create a *compound* run configuration that tells Visual Studio Code which set of configurations to run in parallel.</span></span> 

<span data-ttu-id="25181-219">Fügen Sie den folgenden Codeausschnitt als Eigenschaft der obersten Ebene in der Datei `launch.json` hinzu (als gleichgeordnetes Element der vorhandenen **configurations**-Eigenschaft).</span><span class="sxs-lookup"><span data-stu-id="25181-219">Add the following snippet as a top-level property within the `launch.json` file (as a sibling of the existing **configurations** property).</span></span>

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

<span data-ttu-id="25181-220">Die Zeichenfolgenwerte, die im Array **compounds.configurations** angegeben sind, verweisen auf den Namen (**name**) der einzelnen Einträge in der Liste mit den Konfigurationen (**configurations**).</span><span class="sxs-lookup"><span data-stu-id="25181-220">The string values specified in the **compounds.configurations** array refer to the **name** of individual entries in the list of **configurations**.</span></span> <span data-ttu-id="25181-221">Wenn Sie diese Namen geändert haben, müssen Sie die entsprechenden Änderungen im Array vornehmen.</span><span class="sxs-lookup"><span data-stu-id="25181-221">If you've modfied those names, you'll need to make the appropriate changes in the array.</span></span> <span data-ttu-id="25181-222">Wechseln Sie hierfür zur Registerkarte „Debuggen“, und ändern Sie die ausgewählte Konfiguration in **Full-Stack** (Name der zusammengesetzten Konfiguration). Drücken Sie anschließend **&lt;F5>**, um sie auszuführen.</span><span class="sxs-lookup"><span data-stu-id="25181-222">To see this in action, switch to the debug tab, and change the selected configuration to **Full-Stack** (the name of the compound configuration), and press **&lt;F5>** to run it.</span></span>

![Ausführen einer Konfiguration in Visual Studio Code](./media/node-howto-e2e/full-stack-profile.png)

<span data-ttu-id="25181-224">Durch die Ausführung der Konfiguration werden die Node.js-App (in der Ausgabe der Debugging-Konsole zu sehen) und Chrome (für die Navigation zur Node.js-App unter `http://localhost:8080`) gestartet.</span><span class="sxs-lookup"><span data-stu-id="25181-224">Running the configuration launches the Node.js app (as can be seen in the debug console output) and Chrome (configured to navigate to the Node.js app at `http://localhost:8080`).</span></span>

<span data-ttu-id="25181-225">Drücken Sie **&lt;STRG>+P**, und geben Sie `todos.js` ein (bzw. wählen Sie die Datei aus). Dies ist der Angular-Hauptcontroller für das Front-End der App.</span><span class="sxs-lookup"><span data-stu-id="25181-225">Press **&lt;Ctrl>P**, and enter (or select) `todos.js`, which is the main Angular controller for the app's front-end.</span></span> 

<span data-ttu-id="25181-226">Legen Sie in Zeile 11 einen Breakpoint fest, der als Einstiegspunkt für einen neuen zu erstellenden To-Do-Eintrag dient.</span><span class="sxs-lookup"><span data-stu-id="25181-226">Set a breakpoint on line 11, which is the entry-point for a new todo entry being created.</span></span>

<span data-ttu-id="25181-227">Wechseln Sie zurück zur ausgeführten App, und fügen Sie einen neuen To-Do-Eintrag hinzu. Sie sehen, dass Visual Studio Code die Ausführung im Angular-Code angehalten hat.</span><span class="sxs-lookup"><span data-stu-id="25181-227">Return to the running app, add a new todo entry, and notice that Visual Studio Code has now suspended execution within the Angular code.</span></span>

![Debuggen des Front-End-Codes in Visual Studio Code](./media/node-howto-e2e/chrome-pause.png)

<span data-ttu-id="25181-229">Wie beim Debuggen von Node.js auch, können Sie den Mauszeiger auf Ausdrücke bewegen, lokale Elemente bzw. Überwachungselemente anzeigen, Ausdrücke in der Konsole auswerten usw.</span><span class="sxs-lookup"><span data-stu-id="25181-229">Like Node.js debugging, you can hover your mouse over expressions, view locals/watches, evaluate expressions in the console, and so on.</span></span> 

<span data-ttu-id="25181-230">Beachten Sie zwei interessante Punkte:</span><span class="sxs-lookup"><span data-stu-id="25181-230">There are two cools things to note:</span></span>

1. <span data-ttu-id="25181-231">Im Bereich **Aufrufliste** werden zwei unterschiedliche Listen angezeigt: **Node** und **Chrome**. Außerdem wird angegeben, welche gerade angehalten ist.</span><span class="sxs-lookup"><span data-stu-id="25181-231">The **Call Stack** pane displays two different stacks: **Node** and **Chrome**, and indicates which one is currently paused.</span></span>

1. <span data-ttu-id="25181-232">Sie können zwischen dem Front-End- und Back-End-Code wechseln.</span><span class="sxs-lookup"><span data-stu-id="25181-232">You can step between front and back-end code.</span></span> <span data-ttu-id="25181-233">Drücken Sie hierfür **&lt;F5>**, um die Ausführung zu starten und den Breakpoint zu erreichen, den Sie zuvor in der Express-Route festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="25181-233">To test this, press **&lt;F5>**, which will run and hit the breakpoint previously set in the Express route.</span></span>

<span data-ttu-id="25181-234">Mit diesem Setup können Sie JavaScript-Code vom Typ Front, Back oder Full-Stack direkt in Visual Studio Code debuggen.</span><span class="sxs-lookup"><span data-stu-id="25181-234">With this setup, you can now efficiently debug front, back, or full-stack JavaScript code directly within Visual Studio Code.</span></span> 

<span data-ttu-id="25181-235">Darüber hinaus ist das Konzept des zusammengesetzten Debuggers nicht auf zwei Zielprozesse und auch nicht allein auf JavaScript beschränkt.</span><span class="sxs-lookup"><span data-stu-id="25181-235">In addition, the compound debugger concept is not limited to just two target processes, and also isn't just limited to JavaScript.</span></span> <span data-ttu-id="25181-236">Bei der Arbeit an einer Microservice-App (ggf. eine Polyglot-App) können Sie genau den gleichen Workflow verwenden (nachdem Sie die richtigen Erweiterungen für die Sprache bzw. das Framework installiert haben).</span><span class="sxs-lookup"><span data-stu-id="25181-236">Therefore, if work on a microservice app (that is potentially polyglot), you can use the exact same workflow (once you've installed the appropriate extensions for the language/framework).</span></span>

## <a name="dockerizing-the-app"></a><span data-ttu-id="25181-237">Vorbereiten der App für Docker</span><span class="sxs-lookup"><span data-stu-id="25181-237">Dockerizing the app</span></span>

<span data-ttu-id="25181-238">In diesem Abschnitt geht es um die Benutzeroberfläche, die von Visual Studio Code für die Entwicklung mit [Docker](https://www.docker.com/) bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="25181-238">This section focuses on the experience that Visual Studio Code provides for developing with [Docker](https://www.docker.com/).</span></span> <span data-ttu-id="25181-239">Node.js-Entwickler nutzen Docker, um portable App-Bereitstellungen für Entwicklungs-, Continuous Integration- und Produktionsumgebungen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="25181-239">Node.js developers use Docker to provide portable app deployments for both development, CI (continuous integration), and production environments.</span></span> <span data-ttu-id="25181-240">Da die Nutzung von Docker nicht immer einfach ist, wird in Visual Studio Code durch die Bereitstellung einer Erweiterung versucht, den Einsatz von Docker in Ihren Apps zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="25181-240">As Docker presents a steep-learning curve to some, Visual Studio Code provides an extension that tries to help simplify some using Docker in your apps.</span></span>

<span data-ttu-id="25181-241">Wechseln Sie zurück zur Registerkarte **Erweiterungen**, suchen Sie nach `docker`, und wählen Sie die Erweiterung **Docker** aus.</span><span class="sxs-lookup"><span data-stu-id="25181-241">Switch back to the **Extensions** tab, search for `docker`, and select the **Docker** extension.</span></span> 

<span data-ttu-id="25181-242">Installieren Sie die Docker-Erweiterung, und laden Sie Visual Studio Code dann erneut.</span><span class="sxs-lookup"><span data-stu-id="25181-242">Install the Docker extension, and then reload Visual Studio Code.</span></span>

![Installieren der Docker-Erweiterung für Visual Studio Code](./media/node-howto-e2e/docker-search.png)

<span data-ttu-id="25181-244">Die Docker-Erweiterung für Visual Studio Code enthält einen Befehl zum Generieren einer *Dockerfile* und die Datei `docker-compose.yml` für ein vorhandenes Projekt.</span><span class="sxs-lookup"><span data-stu-id="25181-244">The Docker extension for Visual Studio Code includes a command for generating a *Dockerfile* and the `docker-compose.yml` file for an existing project.</span></span> 

<span data-ttu-id="25181-245">Zeigen Sie zum Auflisten der verfügbaren Docker-Befehle die Befehlspalette an, indem Sie **&lt;F1>** drücken und anschließend `docker` eingeben.</span><span class="sxs-lookup"><span data-stu-id="25181-245">To see the available Docker commands, display the command palette - via **&lt;F1>** - and type `docker`.</span></span>

![<span data-ttu-id="25181-246">Von der Docker-Erweiterung unterstützte Befehle für Visual Studio</span><span class="sxs-lookup"><span data-stu-id="25181-246">Commands supported by the Docker extension for Visual Studio</span></span> ](./media/node-howto-e2e/docker-commands.png)

<span data-ttu-id="25181-247">Wählen Sie **Docker: Add docker files to workspace** (Docker: Docker-Dateien dem Arbeitsbereich hinzufügen), wählen Sie **Node.js** als App-Plattform aus, und geben Sie an, dass für die App der Port `8080` verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="25181-247">Select **Docker: Add docker files to workspace**, select **Node.js** as the app platform, and specify that the app exposes port `8080`.</span></span> 

<span data-ttu-id="25181-248">Mit dem Docker-Befehl werden eine vollständige `Dockerfile` und Docker-Compose-Dateien generiert, die Sie sofort nutzen können.</span><span class="sxs-lookup"><span data-stu-id="25181-248">The Docker command generates a complete `Dockerfile` and Docker-compose files that you can begin using immediately.</span></span>

![Generierte Dockerfile](./media/node-howto-e2e/docker-file.png)

<span data-ttu-id="25181-250">Außerdem ermöglicht die Docker-Erweiterung die automatische Vervollständigung für Ihre Dateien `Dockerfiles` und `docker-compose.yml`.</span><span class="sxs-lookup"><span data-stu-id="25181-250">The Docker extension also provides auto-completion for your `Dockerfiles` and `docker-compose.yml` files.</span></span> 

<span data-ttu-id="25181-251">Öffnen Sie hierzu die `Dockerfile`, und ändern Sie Zeile 2:</span><span class="sxs-lookup"><span data-stu-id="25181-251">To see this in action, open the `Dockerfile` and change line 2 from:</span></span>

```docker
FROM node:latest
```

<span data-ttu-id="25181-252">in:</span><span class="sxs-lookup"><span data-stu-id="25181-252">To:</span></span>

```docker
FROM mhart
```

<span data-ttu-id="25181-253">Positionieren Sie den Cursor nach dem `t` in `mhart`, und drücken Sie **&lt;STRG>+&lt;LEERTASTE>**, um alle Image-Repositorys anzuzeigen, die von `mhart` im DockerHub veröffentlicht wurden.</span><span class="sxs-lookup"><span data-stu-id="25181-253">With your cursor positioned after the `t` in `mhart`, press **&lt;Ctrl>&lt;Space>** to view all the image repositories that `mhart` has published on DockerHub.</span></span>

![Automatische Vervollständigung der Docker-Erweiterung](./media/node-howto-e2e/docker-completion.png)

<span data-ttu-id="25181-255">Wählen Sie `mhart/alpine-node`, um alle Objekte bereitzustellen, die für diese App benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="25181-255">Select `mhart/alpine-node`, which provides everything that this app needs.</span></span> 

<span data-ttu-id="25181-256">Kleinere Images sind normalerweise besser geeignet, da Ihre App-Builds und -Bereitstellungen so schnell wie möglich ablaufen sollen, um die Verteilung und Skalierung zu beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="25181-256">Smaller images are typically better since you want your app builds and deployments to be as fast as possible, which makes distribution and scaling quicker.</span></span>

<span data-ttu-id="25181-257">Nachdem Sie die `Dockerfile` generiert haben, müssen Sie das eigentliche Docker-Image erstellen.</span><span class="sxs-lookup"><span data-stu-id="25181-257">Now, that you have generated the `Dockerfile`, you need to build the actual Docker image.</span></span> <span data-ttu-id="25181-258">Hierfür können Sie wieder einen Befehl verwenden, der von der Docker-Erweiterung in Visual Studio Code installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="25181-258">Once again, you can use a command that the Docker extension installed in Visual Studio Code.</span></span> <span data-ttu-id="25181-259">Drücken Sie **&lt;F1>**, geben Sie in der Befehlspalette den Text `dockerb` ein, und wählen Sie den Befehl **Docker: Build Image** (Docker: Image erstellen).</span><span class="sxs-lookup"><span data-stu-id="25181-259">Press **&lt;F1>**, enter `dockerb` at the command palette, and select the **Docker: Build Image** command.</span></span> <span data-ttu-id="25181-260">Wählen Sie die `/Dockerfile` aus, die Sie gerade generiert und geändert haben.</span><span class="sxs-lookup"><span data-stu-id="25181-260">Choose the `/Dockerfile` that you just generated and modified.</span></span> <span data-ttu-id="25181-261">Geben Sie ein Tag an, das Ihren DockerHub-Benutzernamen enthält (z.B. `lostintangent/node`).</span><span class="sxs-lookup"><span data-stu-id="25181-261">Specify a tag that includes your DockerHub username (e.g. `lostintangent/node`).</span></span> <span data-ttu-id="25181-262">Drücken Sie die **&lt;EINGABETASTE>**, um das integrierte Terminalfenster zu starten, in dem die Ausgabe Ihres zu erstellenden Docker-Image angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="25181-262">Press **&lt;ENTER>** to launch the integrated terminal window that displays the output of your Docker image being built.</span></span>

![Buildstatus des Docker-Image](./media/node-howto-e2e/docker-build.png)

<span data-ttu-id="25181-264">Beachten Sie, dass mit dem Befehl der Prozess zur Ausführung von `docker build` für Sie automatisiert wurde. Dies ist ein weiteres Beispiel für ein Mittel zur Verbesserung der Produktivität, das Sie wählen können, oder Sie können direkt die Docker CLI nutzen.</span><span class="sxs-lookup"><span data-stu-id="25181-264">Notice that the command automated the process of running `docker build` for you, which is another example of a productivity enhancer that you can either choose to use, or you can just use the Docker CLI directly.</span></span> 

<span data-ttu-id="25181-265">An diesem Punkt müssen Sie das Image nur noch per Pushvorgang an DockerHub übermitteln, damit von Bereitstellungen leicht darauf zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="25181-265">At this point, to make this image easily acquirable for deployments, you need only push the image to DockerHub.</span></span> <span data-ttu-id="25181-266">Stellen Sie hierfür sicher, dass Sie die Authentifizierung mit DockerHub bereits durchgeführt haben, indem Sie `docker login` über die CLI ausführen und Ihre Anmeldeinformationen für Ihr Konto eingeben.</span><span class="sxs-lookup"><span data-stu-id="25181-266">To do this, make sure you have already autheticated with DockerHub by running `docker login` from the CLI and entering your account credentials.</span></span> <span data-ttu-id="25181-267">In Visual Studio Code könne Sie dann die Befehlspalette aufrufen, `dockerpush` eingeben und den Befehl `Docker: Push` wählen.</span><span class="sxs-lookup"><span data-stu-id="25181-267">Then, in Visual Studio Code, you can bring up the command palette, enter `dockerpush`, and select the `Docker: Push` command.</span></span> <span data-ttu-id="25181-268">Wählen Sie das Image-Tag aus, das Sie gerade erstellt haben (z.B. `lostintangent/node`), und drücken Sie die **&lt;EINGABETASTE>**.</span><span class="sxs-lookup"><span data-stu-id="25181-268">Select the image tag that you just built (e.g. `lostintangent/node`) and press **&lt;Enter>**.</span></span> <span data-ttu-id="25181-269">Mit dem Befehl wird der Aufruf von `docker push` automatisiert und die Ausgabe im integrierten Terminal angezeigt.</span><span class="sxs-lookup"><span data-stu-id="25181-269">The command automates the calling of `docker push` and displays the output in the integrated terminal.</span></span>

## <a name="deploying-the-app"></a><span data-ttu-id="25181-270">Bereitstellen der App</span><span class="sxs-lookup"><span data-stu-id="25181-270">Deploying the app</span></span>

<span data-ttu-id="25181-271">Nachdem Sie die App für Docker vorbereitet und an DockerHub übermittelt haben, müssen Sie sie in der Cloud bereitstellen, damit sie öffentlich verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="25181-271">Now that you the app Dockerized and pushed to DockerHub, you need to deploy it to the cloud so the world can see it.</span></span> <span data-ttu-id="25181-272">Zu diesem Zweck können Sie Azure App Service nutzen. Dies ist das PaaS-Angebot von Azure.</span><span class="sxs-lookup"><span data-stu-id="25181-272">For this, you can use Azure App Service, which is Azure's PaaS offering.</span></span> <span data-ttu-id="25181-273">App Service verfügt über zwei Funktionen, die für Node.js-Entwickler relevant sind:</span><span class="sxs-lookup"><span data-stu-id="25181-273">App Service has two capabilities that are relevant to Node.js developers:</span></span>

- <span data-ttu-id="25181-274">Unterstützung für Linux-basierte VMs: Reduziert Inkompatibilitäten für Apps, die mit nativen Node-Modulen erstellt werden, oder für andere Tools, die ggf. keine Windows-Unterstützung bzw. ein anderes Verhalten aufweisen.</span><span class="sxs-lookup"><span data-stu-id="25181-274">Support for Linux-based VMs, which reduces incompatibilities for apps which are built using native Node modules, or other tools which might not support Windows and/or may behave differently.</span></span>
- <span data-ttu-id="25181-275">Unterstützung für Docker-basierte Bereitstellungen: Ermöglicht Ihnen das Angeben des Namens Ihres Docker-Image und für App Service das automatische „Pullen“, Bereitstellen und Skalieren des Image.</span><span class="sxs-lookup"><span data-stu-id="25181-275">Support for Docker-based deployments, which allows you to specify the name of your Docker image, and allow App Service to pull, deploy, and scale the image automatically.</span></span>

<span data-ttu-id="25181-276">Öffnen Sie als Erstes das Visual Studio-Terminal.</span><span class="sxs-lookup"><span data-stu-id="25181-276">To get started, open up the Visual Studio terminal.</span></span> <span data-ttu-id="25181-277">Sie verwenden die neue Version „Azure CLI 2.0“, um Ihr Azure-Konto zu verwalten und die erforderliche Infrastruktur zum Ausführen der To-Do-App bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="25181-277">You'll use the new Azure CLI 2.0 to manage your Azure account and provision the necessary infrastructure to run the todo app.</span></span> <span data-ttu-id="25181-278">Nachdem Sie sich über die CLI mit dem Befehl `az login` an Ihrem Konto angemeldet haben (wie in den Voraussetzungen erwähnt), können Sie die folgenden Schritte ausführen, um die App Service-Instanz und den To-Do-App-Container bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="25181-278">Once you've logged into your account from the CLI using the `az login` command (as mentioned in the pre-reqs), perform the following steps to provision the App Service instance and deploy the todo app container:</span></span>

1. <span data-ttu-id="25181-279">Erstellen Sie eine Ressourcengruppe. Diese können Sie sich als *Namespace* oder *Verzeichnis* zur Unterstützung der Organisation von Azure-Ressourcen vorstellen.</span><span class="sxs-lookup"><span data-stu-id="25181-279">Create a resource group, which you can think of as a *namespace* or *directory* for helping to organize Azure resources.</span></span> <span data-ttu-id="25181-280">Die Option `-n` wird verwendet, um den Namen der Gruppe anzugeben. Dies kann ein beliebiger Name sein.</span><span class="sxs-lookup"><span data-stu-id="25181-280">The `-n` option is used to specify the name of the group and can be anything you want.</span></span>

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > <span data-ttu-id="25181-281">Mit der Option `-l` wird der Standort der Ressourcengruppe angegeben.</span><span class="sxs-lookup"><span data-stu-id="25181-281">The `-l` option indicates the location of the resource group.</span></span> <span data-ttu-id="25181-282">Während der Vorschauphase ist die Unterstützung von App Service unter Linux nur in ausgewählten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="25181-282">While in preview, the App Service on Linux support is available only in select regions.</span></span> <span data-ttu-id="25181-283">Wenn Sie nicht im Westen der USA ansässig sind und prüfen möchten, welche anderen Regionen verfügbar sind, können Sie in der CLI daher `az appservice list-locations --linux-workers-enabled` ausführen, um Ihre Optionen für Rechenzentren anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="25181-283">Therefore, if you aren't located in the Western US, and you want to check which other regions are available, run `az appservice list-locations --linux-workers-enabled` from the CLI to view your datacenter options.</span></span>

2. <span data-ttu-id="25181-284">Legen Sie die neu erstellte Ressourcengruppe als Standardressourcengruppe fest, damit Sie die CLI weiter nutzen können, ohne die Ressourcengruppe für jeden CLI-Aufruf explizit angeben zu müssen:</span><span class="sxs-lookup"><span data-stu-id="25181-284">Set the newly created resource group as the default resource group so that you can continue to use the CLI without needing to explicitly specify the resource group with each CLI call:</span></span>

   ```shell
   az configure -d group=nina-demo
   ```
   
3. <span data-ttu-id="25181-285">Erstellen Sie den App Service-*Plan*, über den die Erstellung und Skalierung der zugrunde liegenden virtuellen Computer verwaltet wird, auf denen Ihre App bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="25181-285">Create the App Service *plan*, which manages the creation and scaling of the underlying virtual machines to which your app is deployed.</span></span> <span data-ttu-id="25181-286">Geben Sie für die Option `n` wieder einen beliebigen Wert an.</span><span class="sxs-lookup"><span data-stu-id="25181-286">Once again, specify any value that you'd like for the `n` option.</span></span>

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > <span data-ttu-id="25181-287">Die Option „--is-linux“ gibt an, dass Sie Linux-basierte virtuelle Computer verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="25181-287">The --is-linux option is indicates that you want Linux-based virtual machines.</span></span> <span data-ttu-id="25181-288">Ohne diese Option werden von der CLI standardmäßig Windows-basierte virtuelle Computer bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="25181-288">Without it, the CLI defaults to provisioning Windows-based virtual machines.</span></span>

4. <span data-ttu-id="25181-289">Erstellen Sie die App Service-Web-App, bei der es sich um die eigentliche To-Do-App handelt, die für den eben erstellten Plan und die Ressourcengruppe ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="25181-289">Create the App Service web app, which represents the actual todo app that will be running within the plan and resource group just created.</span></span> <span data-ttu-id="25181-290">Eine Web-App ist praktisch synonym mit einem Prozess oder Container, und der Plan dient als Host für die Ausführung des virtuellen Computers bzw. Containers.</span><span class="sxs-lookup"><span data-stu-id="25181-290">You can think of a web app as being synonymous with a process or container, and the plan as being the virtual machine/container host that they're running on.</span></span> <span data-ttu-id="25181-291">Außerdem müssen Sie im Rahmen der Web-App-Erstellung die Konfiguration so durchführen, dass das von Ihnen auf DockerHub veröffentlichte Docker-Image verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="25181-291">Additionally, as part of creating the web app, you'll need to configure it to use the Docker image you published to DockerHub:</span></span>

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > <span data-ttu-id="25181-292">Wenn Sie anstelle der Verwendung eines benutzerdefinierten Containers eine Git-Bereitstellung vorziehen, helfen Ihnen die Informationen im Artikel [Erstellen einer Node.js-Web-App in Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs) weiter.</span><span class="sxs-lookup"><span data-stu-id="25181-292">If instead of using a custom container, you'd prefer a Git deployment, refer to the article, [Create a Node.js web app in Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).</span></span>

5. <span data-ttu-id="25181-293">Legen Sie die Web-App als Standard-Webinstanz fest:</span><span class="sxs-lookup"><span data-stu-id="25181-293">Set the web app as the default web instance:</span></span>

    ```shell
    az configure -d web=nina-demo-app
    ```

6. <span data-ttu-id="25181-294">Starten Sie die App, um den bereitgestellten Container anzuzeigen, der unter der URL vom Typ `*.azurewebsites.net` verfügbar ist:</span><span class="sxs-lookup"><span data-stu-id="25181-294">Launch the app to view the deployed container, which will be available at an `*.azurewebsites.net` URL:</span></span>

    ```shell
    az webapp browse
    ```

    ![Ausgeführte To-Do-App im Browser](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > <span data-ttu-id="25181-296">Der erste Ladevorgang der App kann einige Minuten dauern, da App Service das Docker-Image per Pullvorgang aus DockerHub abrufen und dann starten muss.</span><span class="sxs-lookup"><span data-stu-id="25181-296">It may take few minutes to load app the first time as App Service has to pull the Docker image from DockerHub and then start it.</span></span>

<span data-ttu-id="25181-297">Sie haben die To-Do-App jetzt bereitgestellt und ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="25181-297">At this point, you've just deployed and run the todo app.</span></span> 

<span data-ttu-id="25181-298">Sie haben die Bereitstellung der To-Do-App jetzt abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="25181-298">You have now deployed the todo app.</span></span> <span data-ttu-id="25181-299">Aber durch das sich drehende Symbol wird angegeben, dass die App keine Verbindung mit der Datenbank herstellen kann.</span><span class="sxs-lookup"><span data-stu-id="25181-299">However, the spinning icon indicates that the app can't connect to the database.</span></span> <span data-ttu-id="25181-300">Dies liegt daran, dass Sie bei der Entwicklung eine lokale Instanz von MongoDB verwendet haben, die aus den Azure-Rechenzentren natürlich nicht erreichbar ist.</span><span class="sxs-lookup"><span data-stu-id="25181-300">This is due to the fact that you were using a local instance of MongoDB during development, which obviously isn't reachable from within the Azure datacenters.</span></span> <span data-ttu-id="25181-301">Da Sie die App so geändert haben, dass die Verbindungszeichenfolge über eine Umgebungsvariable akzeptiert wird, müssen Sie nur einen MongoDB-Server starten und die App Service-Instanz so konfigurieren, dass auf die Umgebungsvariable verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="25181-301">Since you modified the app to accept the connection string via an environment variable, you need only to start a MongoDB server and re-configure the App Service instance to reference the environment variable.</span></span> <span data-ttu-id="25181-302">Dies wird im nächsten Abschnitt veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="25181-302">This is illustrated in the next section.</span></span>

## <a name="provisioning-a-mongodb-server"></a><span data-ttu-id="25181-303">Bereitstellen eines MongoDB-Servers</span><span class="sxs-lookup"><span data-stu-id="25181-303">Provisioning a MongoDB server</span></span>

<span data-ttu-id="25181-304">Sie können zwar einen MongoDB-Server oder eine Replikatgruppe konfigurieren und diese Infrastruktur selbst verwalten, aber in Azure ist hierfür eine Lösung mit dem Namen [Cosmos DB](https://azure.microsoft.com/services/documentdb/) vorhanden.</span><span class="sxs-lookup"><span data-stu-id="25181-304">While you could configure a MongoDB server, or replica set, and manage that infrastructure yourself, Azure provides a solution called [Cosmos DB](https://azure.microsoft.com/services/documentdb/).</span></span> <span data-ttu-id="25181-305">Bei Cosmos DB handelt es sich um eine vollständig verwaltete NoSQL-Datenbank mit Georeplikation und hoher Leistung, über die eine MongoDB-Kompatibilitätsebene bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="25181-305">Cosmos DB is a fully-managed, geo-replicable, high-performance, NoSQL database that provides a MongoDB-compatibility layer.</span></span> <span data-ttu-id="25181-306">Dies bedeutet, dass Sie für eine vorhandene MEAN-App darauf verweisen können (oder einen beliebigen MongoDB-Client bzw. ein MongoDB-Tool, z.B. [Studio 3T](https://studio3t.com/)), ohne dass Sie außer der Verbindungszeichenfolge etwas ändern müssen.</span><span class="sxs-lookup"><span data-stu-id="25181-306">This means that you can point an existing MEAN app at it (or any MongoDB client/tool such as [Studio 3T](https://studio3t.com/)) without needing to change anything but the connection string.</span></span> <span data-ttu-id="25181-307">Die folgenden Schritte veranschaulichen die Vorgehensweise:</span><span class="sxs-lookup"><span data-stu-id="25181-307">The following steps illustrate how this is done:</span></span>

1. <span data-ttu-id="25181-308">Führen Sie im Visual Studio Code-Terminal den folgenden Befehl aus, um eine MongoDB-kompatible Instanz des Cosmos DB-Diensts zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="25181-308">From the Visual Studio Code terminal, run the following command to create a MongoDB-compatible instance of the Cosmos DB service.</span></span> <span data-ttu-id="25181-309">Ersetzen Sie den Platzhalter **<NAME>** durch einen global eindeutigen Wert (Cosmos DB nutzt diesen Namen zum Generieren der Server-URL einer Datenbank):</span><span class="sxs-lookup"><span data-stu-id="25181-309">Replace the **<NAME>** placeholder with a globally unique value (Cosmos DB uses this name to generate the database's server URL):</span></span>

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. <span data-ttu-id="25181-310">Rufen Sie die MongoDB-Verbindungszeichenfolge für diese Instanz ab:</span><span class="sxs-lookup"><span data-stu-id="25181-310">Retrieve the MongoDB connection string for this instance:</span></span>

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. <span data-ttu-id="25181-311">Aktualisieren Sie die Umgebungsvariable **MONGODB_URL** Ihrer Web-App so, dass eine Verbindung mit der neu bereitgestellten Cosmos DB-Instanz hergestellt und nicht versucht wird, eine Verbindung mit einem lokal ausgeführten MongoDB-Server (der nicht existiert!) herzustellen:</span><span class="sxs-lookup"><span data-stu-id="25181-311">Update your web app's **MONGODB_URL** environment variable so that it connects to the newly provisioned Cosmos DB instance instead of attempting to connect to a locally running MongoDB server (that doesn't exist!):</span></span>

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. <span data-ttu-id="25181-312">Wechseln Sie zurück in Ihren Browser, und aktualisieren Sie die Anzeige.</span><span class="sxs-lookup"><span data-stu-id="25181-312">Return to your browser and refresh it.</span></span> <span data-ttu-id="25181-313">Versuchen Sie, ein To-Do-Element hinzuzufügen und zu entfernen, um zu bestätigen, dass die App jetzt funktioniert, ohne dass etwas geändert werden muss.</span><span class="sxs-lookup"><span data-stu-id="25181-313">Try adding and removing a todo item to prove that the app now works without needing to change anything!</span></span> <span data-ttu-id="25181-314">Legen Sie die Umgebungsvariable auf die erstellte Cosmos DB-Instanz fest, bei der es sich um eine vollständige Emulation einer MongoDB-Datenbank handelt.</span><span class="sxs-lookup"><span data-stu-id="25181-314">Set the environment variable to the created Cosmos DB instance, which is fully emulating a MongoDB database.</span></span>

    ![Demo-App nach Verbindungsherstellung mit einer Datenbank](./media/node-howto-e2e/finished-demo.png)

<span data-ttu-id="25181-316">Bei Bedarf können Sie zurück zur Cosmos DB-Instanz wechseln und den reservierten Durchsatz, der für die MongoDB-Instanz benötigt wird, zentral hochskalieren (oder zentral herunterskalieren). So profitieren Sie von dem zusätzlichen Datenverkehr, ohne dass Sie Elemente der Infrastruktur manuell verwalten müssen.</span><span class="sxs-lookup"><span data-stu-id="25181-316">When needed, you can switch back to the Cosmos DB instance and scale up (or down) the reserved throughput that the MongoDB instance needs, and benefit from the added traffic without needing to manage any infrastructure manually.</span></span>

<span data-ttu-id="25181-317">Außerdem indiziert Cosmos DB automatisch jedes einzelne Dokument und jede Eigenschaft für Sie.</span><span class="sxs-lookup"><span data-stu-id="25181-317">Additionally, Cosmos DB automatically indexes every single document and property for you.</span></span> <span data-ttu-id="25181-318">Sie müssen dann keine Profile für langsame Abfragen erstellen und Ihre Indizes nicht manuell optimieren.</span><span class="sxs-lookup"><span data-stu-id="25181-318">That way, you don't need to profile slow queries or manually fine-tune your indexes.</span></span> <span data-ttu-id="25181-319">Führen Sie die Bereitstellung und Skalierung einfach nach Bedarf durch, und überlassen Sie Cosmos DB den Rest.</span><span class="sxs-lookup"><span data-stu-id="25181-319">Just provision and scale as needed, and let Cosmos DB handle the rest.</span></span>

## <a name="hosting-a-private-docker-registry"></a><span data-ttu-id="25181-320">Hosten einer privaten Docker-Registrierung</span><span class="sxs-lookup"><span data-stu-id="25181-320">Hosting a private Docker registry</span></span>

<span data-ttu-id="25181-321">DockerHub stellt eine hervorragende Benutzeroberfläche für die Verteilung Ihrer Containerimages bereit. Es kann aber Fälle geben, in denen Sie es vorziehen, Ihre eigene private Docker-Registrierung zu hosten, z.B. im Sicherheits- oder Governance-Bereich oder zur Erzielung von Leistungsvorteilen.</span><span class="sxs-lookup"><span data-stu-id="25181-321">DockerHub provides an amazing experience for distributing your container images, but there may be scenarios where you'd prefer to host your own private Docker registry - such as for security/governance or performance benefits.</span></span> <span data-ttu-id="25181-322">Für diese Zwecke enthält Azure die [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR), mit der Sie Ihre eigene Docker-Registrierung erstellen können. Der Hintergrundspeicher befindet sich hierbei in demselben Datencenter wie Ihre Web-App (ermöglicht schnellere Pullvorgänge).</span><span class="sxs-lookup"><span data-stu-id="25181-322">For this purpose, Azure provides the [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR) that allows you to spin up your own Docker registry whose backing storage is located in the same data center as your web app (which makes pulls quicker).</span></span> <span data-ttu-id="25181-323">Mit der ACR haben Sie außerdem die volle Kontrolle über den Inhalt und die Zugriffssteuerung und können beispielsweise festlegen, welche Benutzer Push- bzw. Pullvorgänge für Images durchführen können.</span><span class="sxs-lookup"><span data-stu-id="25181-323">The ACR also provides you with full control over the contents and access controls - such as who can push or pull images.</span></span> 

<span data-ttu-id="25181-324">Sie können eine benutzerdefinierte Registrierung bereitstellen, indem Sie den folgenden Befehl ausführen.</span><span class="sxs-lookup"><span data-stu-id="25181-324">Provisioning a custom registry can be accomplished by running the following command.</span></span> <span data-ttu-id="25181-325">(Ersetzen Sie den Platzhalter **<NAME>** durch einen global eindeutigen Wert, da die ACR einen angegebenen Wert verwendet, um die Anmeldeserver-URL der Registrierung zu generieren.)</span><span class="sxs-lookup"><span data-stu-id="25181-325">(Replace the **<NAME>** placeholder with a globally unique value as ACR uses specified value to generate the registry's login server URL.</span></span>

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> <span data-ttu-id="25181-326">Im Beispiel in diesem Thema wird der Einfachheit halber das **Konto „admin“** verwendet. Für Registrierungen, die für die Produktion bestimmt sind, ist dies aber nicht zu empfehlen.</span><span class="sxs-lookup"><span data-stu-id="25181-326">While this topic's example uses the **admin account** to keep things simple, it is not recommended for production registries.</span></span> 

<span data-ttu-id="25181-327">Mit dem Befehl `az acr create` wird die Anmeldeserver-URL angezeigt (Spalte `LOGIN SERVER`), die Sie für die Anmeldung mit der Docker CLI nutzen (z.B. `ninademo.azurecr.io`).</span><span class="sxs-lookup"><span data-stu-id="25181-327">The `az acr create` commands displays the login server URL (via the `LOGIN SERVER` column) that you use to log in using the Docker CLI (e.g. `ninademo.azurecr.io`).</span></span> <span data-ttu-id="25181-328">Außerdem werden mit dem Befehl Administratoranmeldeinformationen generiert, die Sie für die Authentifizierung verwenden können.</span><span class="sxs-lookup"><span data-stu-id="25181-328">Additionally, the command generates admin credentials that you can use in order to authenticate against it.</span></span> <span data-ttu-id="25181-329">Führen Sie zum Abrufen dieser Anmeldeinformationen den folgenden Befehl aus, und notieren Sie sich den angezeigten Benutzernamen und das Kennwort:</span><span class="sxs-lookup"><span data-stu-id="25181-329">To retrieve those credentials, run the following command and note the displayed username and password:</span></span>

```shell
az acr credential show -n $ACR_NAME
```

<span data-ttu-id="25181-330">Mit den Anmeldeinformationen aus dem vorherigen Schritt und Ihrem individuellen Anmeldeserver können Sie sich an der Registrierung anmelden, indem Sie den Docker CLI-Standardworkflow verwenden.</span><span class="sxs-lookup"><span data-stu-id="25181-330">Using the credentials from the previous step, and your individual login server, you can log in to the registry using the standard Docker CLI workflow.</span></span>

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

<span data-ttu-id="25181-331">Sie können Ihren Docker-Container jetzt mit einem Tag versehen, um anzugeben, dass er Ihrer privaten Registrierung zugeordnet ist. Verwenden Sie hierfür den folgenden Befehl, und ersetzen Sie `lostintangent/node` durch den Namen, den Sie dem Containerimage gegeben haben.</span><span class="sxs-lookup"><span data-stu-id="25181-331">You can now tag your Docker container to indicate that it's associated with your private registry using the following command (replacing `lostintangent/node` with the name you gave the container image.</span></span>

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="25181-332">Übertragen Sie das getaggte Image schließlich per Pushvorgang in Ihre private Docker-Registrierung.</span><span class="sxs-lookup"><span data-stu-id="25181-332">Finally, push the tagged image to your private Docker registry.</span></span>

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="25181-333">Ihr Container ist jetzt in Ihrer eigenen privaten Registrierung gespeichert, und die Docker CLI lässt zu, dass Sie genauso wie bei der Verwendung von DockerHub weiterarbeiten.</span><span class="sxs-lookup"><span data-stu-id="25181-333">Your container is now stored in your own private registry, and the Docker CLI was happy to allow you to continue working in the same way as you did when using DockerHub.</span></span> <span data-ttu-id="25181-334">Sie müssen nur den folgenden Befehl ausführen, um die App Service-Web-App anzuweisen, den Pullvorgang aus Ihrer privaten Registrierung durchzuführen:</span><span class="sxs-lookup"><span data-stu-id="25181-334">In order to instruct the App Service web app to pull from your private registry, you need only run the following command:</span></span>

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> <span data-ttu-id="25181-335">Fügen Sie am Anfang der Option `-r` das Präfix `https://` hinzu.</span><span class="sxs-lookup"><span data-stu-id="25181-335">Make sure to add the `https://` prefix to the beginning of the `-r` option.</span></span> <span data-ttu-id="25181-336">Achten Sie aber darauf, dass Sie das Präfix nicht dem Namen des Containerimage hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="25181-336">However, don't add the prefix to the container image name.</span></span>

<span data-ttu-id="25181-337">Wenn Sie die App im Browser aktualisieren, sollte alles gleich aussehen und funktionieren.</span><span class="sxs-lookup"><span data-stu-id="25181-337">If you refresh the app in your browser, everything should look and work the same.</span></span> <span data-ttu-id="25181-338">Jetzt wird Ihre App aber über Ihre private Docker-Registrierung ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="25181-338">However, it's now running your app via your private Docker registry.</span></span> <span data-ttu-id="25181-339">Nachdem Sie die Aktualisierung Ihrer App abgeschlossen haben, können Sie sie wie oben mit einem Tag versehen und die Änderungen per Pushvorgang übertragen und das Tag dann in Ihrer App Service-Containerkonfiguration aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="25181-339">Once you update your app, tag and push the changes as done above, and update the tag in your App Service container configuration.</span></span>

## <a name="configuring-a-custom-domain-name"></a><span data-ttu-id="25181-340">Konfigurieren eines benutzerdefinierten Domänennamens</span><span class="sxs-lookup"><span data-stu-id="25181-340">Configuring a custom domain name</span></span>

<span data-ttu-id="25181-341">Die URL `*.azurewebsites.net` ist zwar gut für Tests geeignet, aber später kann es dann ratsam sein, Ihrer Web-App einen benutzerdefinierten Domänennamen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="25181-341">While the `*.azurewebsites.net` URL is great for testing, at some point you may want to add a custom domain name to your web app.</span></span> <span data-ttu-id="25181-342">Nachdem Sie von einer Registrierungsstelle einen Domänennamen erhalten haben, müssen Sie ihm nur einen `A`-Eintrag hinzufügen, mit dem auf die externe IP (eigentlich ein Lastenausgleich) Ihrer Web-App verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="25181-342">Once you have a domain name from a registrar, you need only add an `A` record to it  that points at your web app's external IP (which is actually a load balancer).</span></span> <span data-ttu-id="25181-343">Sie können diese IP abrufen, indem Sie den folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="25181-343">You can retrieve this IP by running the following command:</span></span>

```shell
az webapp config hostname get-external-ip
```

<span data-ttu-id="25181-344">Zusätzlich zu einem `A`-Eintrag müssen Sie Ihrer Domäne auch einen `TXT`-Eintrag hinzufügen, mit dem auf die bisher verwendete Domäne `*.azurewebsites.net` verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="25181-344">In addition to add an `A` record, you also need to add a `TXT` record to your domain that points at the `*.azurewebsites.net` domain you've been using thus far.</span></span> <span data-ttu-id="25181-345">Anhand der Kombination der `A`- und `TXT`-Einträge kann Azure bestätigen, dass Sie der Besitzer der Domäne sind.</span><span class="sxs-lookup"><span data-stu-id="25181-345">The combination of the `A` and `TXT` records allows Azure to verify that you own the domain.</span></span>

<span data-ttu-id="25181-346">Nachdem diese Einträge erstellt – und die DNS-Änderungen weitergegeben – wurden, können Sie die benutzerdefinierte Domäne bei Azure registrieren, damit alles richtig für den eingehenden Datenverkehr vorbereitet ist.</span><span class="sxs-lookup"><span data-stu-id="25181-346">Once those records are created - and the DNS changes have propagated - register the custom domain with Azure so that it knows to expect the incoming traffic correctly.</span></span> 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> <span data-ttu-id="25181-347">Der Befehl funktioniert erst, nachdem die DNS-Änderungen weitergegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="25181-347">The command will not work until the DNS changes have propagated.</span></span>

<span data-ttu-id="25181-348">Öffnen Sie einen Browser, und navigieren Sie zu Ihrer benutzerdefinierten Domäne, um zu prüfen, ob nun die Auflösung zu Ihrer bereitgestellten App in Azure durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="25181-348">Open a browser and navigate to your custom domain to see that it now resolves to your deployed app on Azure.</span></span>

## <a name="scaling-up-and-out"></a><span data-ttu-id="25181-349">Zentrales Hochskalieren und horizontales Hochskalieren</span><span class="sxs-lookup"><span data-stu-id="25181-349">Scaling up and out</span></span>

<span data-ttu-id="25181-350">Unter Umständen erreicht Ihre Web-App nach einiger Zeit eine so große Beliebtheit, dass ihre zugeordneten Ressourcen (CPU und RAM) nicht mehr ausreichen, um den vermehrten Datenverkehr und die Betriebsanforderungen zu bewältigen.</span><span class="sxs-lookup"><span data-stu-id="25181-350">At some point, your web app may become popular enough that its allocated resources (CPU and RAM) aren't sufficient for handling the increase in traffic and operational demands.</span></span> <span data-ttu-id="25181-351">Der App Service-Plan, den Sie weiter oben erstellt haben (**B1**), verfügt über einen CPU-Kern und 1,75 GB RAM. Damit ist die Auslastungsgrenze relativ schnell erreicht.</span><span class="sxs-lookup"><span data-stu-id="25181-351">The App Service Plan that you created earlier (**B1**) comes with 1 CPU core and 1.75 GB of RAM, which can get maxed out fairly quickly.</span></span> <span data-ttu-id="25181-352">Der Plan **B2** verfügt über doppelt so hohe RAM- und CPU-Werte. Wenn Sie merken, dass einer der Werte für Ihre App nicht mehr ausreicht, können Sie den zugrunde liegenden virtuellen Computer also zentral hochskalieren, indem Sie den folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="25181-352">The **B2** plan come swith twice as much RAM and CPU, so if you notice that your app is beginning to run out of either, you can scale up the underlying virtual machine by running the following command:</span></span>

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> <span data-ttu-id="25181-353">Preisangaben und Spezifikationen für Azure-App-Pläne finden Sie im Artikel [App Service – Preise](https://azure.microsoft.com/pricing/details/app-service/).</span><span class="sxs-lookup"><span data-stu-id="25181-353">For Azure App Plan pricing details and specs, see the article, [App Service Pricing](https://azure.microsoft.com/pricing/details/app-service/)</span></span>

<span data-ttu-id="25181-354">Nach kurzer Zeit wird Ihre Web-App zu der angeforderten Hardware migriert, und die zugeordneten Ressourcen können genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="25181-354">After just a few moments, your web app will be migrated to the requested hardware, and can begin taking advantage of the associated resources.</span></span> <span data-ttu-id="25181-355">Sie können nicht nur zentral hochskalieren, sondern auch zentral herunterskalieren, indem Sie den gleichen Befehl wie oben ausführen. Geben Sie hierbei aber die Option `--sku` an, damit weniger Ressourcen zu einem geringeren Preis bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="25181-355">In addition to scaling up, you can also scale down by running the same command as above, specifying a `--sku` option that provides less resources at a lower price.</span></span> 

<span data-ttu-id="25181-356">Zusätzlich zum zentralen Hochskalieren der Spezifikationen für den virtuellen Computer können Sie Ihre Web-App auch *horizontal hochskalieren* (sofern die Web-App zustandslos ist), indem Sie weitere zugrunde liegende VM-Instanzen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="25181-356">In addition to scaling up the virtual machine specs, as long as your web app is stateless, you also have the option to *scale out* by adding more underlying virtual machine instances.</span></span> <span data-ttu-id="25181-357">Der weiter oben erstellte App Service-Plan enthält nur einen virtuellen Computer (einen *Worker*). Daher wird der gesamte eingehende Datenverkehr letztendlich durch die Grenzwerte der verfügbaren Ressourcen dieser einen Instanz begrenzt.</span><span class="sxs-lookup"><span data-stu-id="25181-357">The App Service Plan you created earlier included only a single virtual machine (a *worker*), and therefore, all incoming traffic is ultimately bound by the limits of the available resources of that one instance.</span></span> <span data-ttu-id="25181-358">Wenn Sie eine zweite VM-Instanz hinzufügen möchten, können Sie den gleichen Befehl wie oben ausführen und nun anstelle der SKU die Anzahl von virtuellen Workercomputern horizontal hochskalieren.</span><span class="sxs-lookup"><span data-stu-id="25181-358">If you want to add a second virtual machine instance, you could run the same command you ran earlier, but instead of scaling up the SKU, you scale out the number of worker virtual machines.</span></span>

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

<span data-ttu-id="25181-359">Wenn Sie eine Web-App auf diese Weise horizontal hochskalieren, wird für den eingehenden Datenverkehr auf transparente Weise für alle Instanzen ein Lastenausgleich durchgeführt. So können Sie Ihre Kapazität sofort erhöhen, ohne dass Sie Code ändern oder sich Gedanken zur erforderlichen Infrastruktur machen müssen.</span><span class="sxs-lookup"><span data-stu-id="25181-359">When you scale out a web app like this, incoming traffic will be transparently load balanced between all instances, which allows you to immediately increase your capacity without any code changes or worrying about the needed infrastructure.</span></span> 

<span data-ttu-id="25181-360">Die Verwendung von zustandslosen Web-Apps wird als bewährte Methode angesehen. Sie machen die Möglichkeit zum Skalieren (zentral hoch, zentral herunter, horizontal hoch) vollständig deterministisch, da kein einzelner virtueller Computer oder eine App-Instanz einen Zustand aufweist, der für den korrekten Betrieb erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="25181-360">Stateless web apps are considered a best practice as they make the ability to scale them (up, down, out) entirely deterministic as no single virtual machine or app instance includes state that is neccessary in order to function.</span></span> 

> [!NOTE]
> <span data-ttu-id="25181-361">Im Tutorial dieses Themas wird die Ausführung einer einzelnen Web-App im Rahmen eines App Service-Plans veranschaulicht. Sie können aber mehrere Web-Apps unter demselben Plan erstellen und bereitstellen, sodass Sie bei Bedarf auch einen einzelnen Plan bereitstellen können und dann nur dafür zahlen müssen.</span><span class="sxs-lookup"><span data-stu-id="25181-361">While this topic's tutorial illustrates running a single web app as part of an App Service Plan, you can create and deploy multiple web apps into the same plan, allowing you to provision and pay for a single plan.</span></span> 

## <a name="clean-up"></a><span data-ttu-id="25181-362">Bereinigung</span><span class="sxs-lookup"><span data-stu-id="25181-362">Clean-up</span></span>

<span data-ttu-id="25181-363">Um sicherzustellen, dass Ihnen für nicht genutzte Azure-Ressourcen keine Kosten berechnet werden, können Sie im Visual Studio Code-Terminal den folgenden Befehl ausführen. Mit dem Befehl werden alle Ressourcen gelöscht, die während dieses Tutorials bereitgestellt wurden.</span><span class="sxs-lookup"><span data-stu-id="25181-363">To ensure that you don't get charged for any Azure resources you aren't using, run the following command from your Visual Studio Code terminal to delete all of the resources provisioned during this tutorial.</span></span>

```shell
az group delete
```

> [!NOTE]
> <span data-ttu-id="25181-364">Es kann einige Minuten dauern, bis der Bereinigungsvorgang abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="25181-364">The clean-up process can take several minutes to complete.</span></span> 

<span data-ttu-id="25181-365">Nach Abschluss des Vorgangs befindet sich Ihr Azure-Konto mit dem Befehl `az group delete` in dem gleichen Zustand wie vor Beginn des Tutorials.</span><span class="sxs-lookup"><span data-stu-id="25181-365">Once finished, the `az group delete` command leaves your Azure account in the same state it was before you started the tutorial.</span></span> <span data-ttu-id="25181-366">Die Möglichkeit, Azure-Ressourcen als einzelne Einheit zu organisieren, bereitzustellen und zu löschen, ist einer der Hauptvorteile von Ressourcengruppen.</span><span class="sxs-lookup"><span data-stu-id="25181-366">The ability to organize, deploy, and delete Azure resources as a single unit is one of the primary benefits of resource groups.</span></span> <span data-ttu-id="25181-367">Daher wird empfohlen, Ressourcen zu gruppieren, für die Sie die gleiche Lebensdauer erwarten.</span><span class="sxs-lookup"><span data-stu-id="25181-367">Therefore, as a recommended practice,  you should group your resources together that you anticipate having the same lifespan.</span></span>