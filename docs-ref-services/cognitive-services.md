---
title: Azure Cognitive Services-Module für Node.js
description: Referenz zu Azure Cognitive Services-Modulen für Node.js
author: brapel
ms.author: v-brapel
manager: ehansen
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fb0319965f7ea9d1bcab25e0e213998052b78ae0
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2018
ms.locfileid: "52144899"
---
# <a name="javascript-azure-cognitive-services-modules"></a>Azure Cognitive Services-Module: JavaScript

## <a name="vision-modules"></a>Bildanalysemodul

### <a name="computer-vision"></a>Maschinelles Sehen 

Gibt Informationen zu visuellen Inhalten in einem Bild zurück:

- Nutzen Sie Tagging, Beschreibungen und bereichspezifische Modelle, um Inhalte zu identifizieren und zuverlässig zu kennzeichnen.
- Wenden Sie Einstellungen für nicht jugendfreie oder anzügliche Inhalte an, um eine automatische Einschränkung dieser Inhalte zu ermöglichen.
- Bestimmen Sie Bildtypen und Farbschemas in Bildern.

Testen Sie [maschinelles Sehen](https://azure.microsoft.com/services/cognitive-services/computer-vision/) kostenlos in Ihrem Browser.

Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:

```
npm install azure-cognitiveservices-computervision
```

[Weitere Informationen](/azure/cognitive-services/computer-vision/home) zur Maschinelles Sehen-API und erste Schritte mit dem [Schnellstart für die Maschinelles Sehen-API mit JavaScript](/azure/cognitive-services/computer-vision/quickstarts/javascript)

### <a name="content-moderator"></a>Content Moderator

Computergestützte Moderation von Texten, Videos und Bildern, erweitert um Tools für die Überprüfung durch Personen.

Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:

```
npm install azure-cognitiveservices-contentmoderator
```

[Weitere Informationen](/azure/cognitive-services/content-moderator/overview) zum Content Moderator-Dienst

### <a name="face-api"></a>Gesichtserkennungs-API

Nutzen Sie die Erkennung, Analyse, Organisation und Markierung von Gesichtern auf Fotos. 

Testen Sie die [Gesichtserkennungs-API](https://azure.microsoft.com/services/cognitive-services/face/) in Ihrem Browser.

Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:

```
npm install azure-cognitiveservices-face
```

[Weitere Informationen](/azure/cognitive-services/face/overview) zur Gesichtserkennungs-API und erste Schritte mit dem [Schnellstart für die Gesichtserkennungs-API mit JavaScript](/azure/cognitive-services/Face/quickstarts/javascript)

## <a name="search-modules"></a>Suchmodule

### <a name="web-search"></a>Websuche

Rufen Sie durch die Bing-Websuche-API indizierte Webdokumente ab, und grenzen Sie die Ergebnisse anhand des Ergebnistyps, der Aktualität und anderer Faktoren ein. 

Testen Sie die [Websuche-API](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) in Ihrem Browser.

Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:

```
npm install azure-cognitiveservices-websearch
```

[Weitere Informationen](/azure/cognitive-services/bing-web-search/overview) zur Bing-Websuche-API und erste Schritte mit dem [Schnellstart für die Websuche-API mit Node.js](/azure/cognitive-services/bing-web-search/quickstarts/nodejs)

### <a name="image-search"></a>Bildersuche

Suchen Sie nach Bildern, und erhalten Sie Ergebnisse mit Miniaturansichten, vollständigen URLs von Bildern, Bildmetadaten und vielem mehr.

Testen Sie die [Bildersuche-API](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) in Ihrem Browser.

Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:

```
npm install azure-cognitiveservices-imagesearch
```

[Weitere Informationen](/azure/cognitive-services/bing-image-search/overview) zur Bing-Bildersuche-API und erste Schritte mit dem [Schnellstart für die Bildersuche-API mit Node.js](/azure/cognitive-services/bing-image-search/quickstarts/nodejs)


### <a name="entity-search"></a>Entitätssuche

Suchen Sie nach der relevantesten Entität (Orte, Personen oder Dinge) für einen bestimmten Suchbegriff oder Ort.

Testen Sie die [Entitätssuche-API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) in Ihrem Browser.

Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:

```
npm install azure-cognitiveservices-entitysearch
```

[Weitere Informationen](/azure/cognitive-services/bing-entities-search/search-the-web) zur Bing-Entitätssuche-API und erste Schritte mit dem [Schnellstart für die Entitätssuche-API mit Node.js](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs)

### <a name="custom-search"></a>Benutzerdefinierte Suche

Erstellen Sie eine benutzerdefinierte Websuche für Ihren spezifischen Suchbereich.

Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:

```
npm install azure-cognitiveservices-customsearch
```

[Weitere Informationen](/azure/cognitive-services/bing-custom-search/) zum Dienst für die benutzerdefinierte Bing-Suche und erste Schritte beim Abfragen der benutzerdefinierten Suche für Ihre Apps mit dem [Schnellstart für die API für die benutzerdefinierte Suche mit Node.js](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs)

### <a name="video-search"></a>Videosuche

Finden Sie Videos überall im Web, und erhalten Sie Ergebnisse mit Metadaten wie Ersteller, Codierungsformat, Länge und Aufrufe.

Testen Sie die [Videosuche-API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) in Ihrem Browser.

Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:

```
npm install azure-cognitiveservices-videosearch
```

[Weitere Informationen](/azure/cognitive-services/bing-video-search/search-the-web) zum Bing-Videosuchdienst und erste Schritte mit dem [Schnellstart für die Videosuche-API mit Node.js](/azure/cognitive-services/bing-video-search/nodejs)


### <a name="news-search"></a>News-Suche

Durchsuchen Sie das Web nach Nachrichtenartikeln, und nutzen Sie Metadaten zu Artikeln, zugehörigen News, Bildern und Informationen zur Quelle.

Testen Sie die [News-Suche-API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) in Ihrem Browser.

Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:

```
npm install azure-cognitiveservices-newssearch
```

[Weitere Informationen](/azure/cognitive-services/bing-news-search/search-the-web) zum Bing-Dienst für die News-Suche und erste Schritte mit dem [Schnellstart für die News-Suche-API mit JavaScript](/azure/cognitive-services/bing-news-search/nodejs)


## <a name="language-modules"></a>Sprachmodule

### <a name="text-analytics"></a>Textanalyse 

Die Textanalyse-API ist ein cloudbasierter Dienst für die Verarbeitung natürlicher Sprache aus unformatiertem Text. Die API bietet drei Hauptfunktionen:

- Stimmungsanalyse
- Schlüsselwortextraktion
- Spracherkennung

Testen Sie die [Textanalyse-API](https://azure.microsoft.com/services/cognitive-services/text-analytics/) in Ihrem Browser.

Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:

```
npm install azure-cognitiveservices-textanalytics
```

[Weitere Informationen](/azure/cognitive-services/text-analytics/overview) zur Textanalyse-API und erste Schritte mit dem [Schnellstart für die Textanalyse-API mit Node.js](/azure/cognitive-services/text-analytics/quickstarts/nodejs)


### <a name="spell-check"></a>Rechtschreibprüfung

Überprüfen Sie mit der Bing-Rechtschreibprüfungs-API Grammatik und Rechtschreibung im Kontext.

Testen Sie die [Rechtschreibprüfungs-API](https://azure.microsoft.com/services/cognitive-services/spell-check/) in Ihrem Browser.

Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:

```
npm install azure-cognitiveservices-spellcheck
```

[Weitere Informationen](/azure/cognitive-services/bing-spell-check/proof-text) zur Rechtschreibprüfungs-API und erste Schritte mit dem [Schnellstart für die Rechtschreibprüfungs-API mit Node.js](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs)

## <a name="samples"></a>Beispiele

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
