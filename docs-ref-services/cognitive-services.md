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
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50272683"
---
# <a name="javascript-azure-cognitive-services-modules"></a><span data-ttu-id="90b1e-103">Azure Cognitive Services-Module: JavaScript</span><span class="sxs-lookup"><span data-stu-id="90b1e-103">JavaScript Azure Cognitive Services modules</span></span>

## <a name="vision-modules"></a><span data-ttu-id="90b1e-104">Bildanalysemodul</span><span class="sxs-lookup"><span data-stu-id="90b1e-104">Vision modules</span></span>

### <a name="computer-vision"></a><span data-ttu-id="90b1e-105">Maschinelles Sehen</span><span class="sxs-lookup"><span data-stu-id="90b1e-105">Computer Vision</span></span> 

<span data-ttu-id="90b1e-106">Gibt Informationen zu visuellen Inhalten in einem Bild zurück:</span><span class="sxs-lookup"><span data-stu-id="90b1e-106">Returns information about visual content found in an image:</span></span>

- <span data-ttu-id="90b1e-107">Nutzen Sie Tagging, Beschreibungen und bereichspezifische Modelle, um Inhalte zu identifizieren und zuverlässig zu kennzeichnen.</span><span class="sxs-lookup"><span data-stu-id="90b1e-107">Use tagging, descriptions, and domain-specific models to identify content and label it with confidence.</span></span>
- <span data-ttu-id="90b1e-108">Wenden Sie Einstellungen für nicht jugendfreie oder anzügliche Inhalte an, um eine automatische Einschränkung dieser Inhalte zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="90b1e-108">Apply adult/racy settings to enable automated restriction of adult content.</span></span>
- <span data-ttu-id="90b1e-109">Bestimmen Sie Bildtypen und Farbschemas in Bildern.</span><span class="sxs-lookup"><span data-stu-id="90b1e-109">Identify image types and color schemes in pictures.</span></span>

<span data-ttu-id="90b1e-110">Testen Sie [maschinelles Sehen](https://azure.microsoft.com/services/cognitive-services/computer-vision/) kostenlos in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="90b1e-110">[Try Computer Vision](https://azure.microsoft.com/services/cognitive-services/computer-vision/) for free in your browser.</span></span>

<span data-ttu-id="90b1e-111">Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:</span><span class="sxs-lookup"><span data-stu-id="90b1e-111">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-computervision
```

<span data-ttu-id="90b1e-112">[Weitere Informationen](/azure/cognitive-services/computer-vision/home) zur Maschinelles Sehen-API und erste Schritte mit dem [Schnellstart für die Maschinelles Sehen-API mit JavaScript](/azure/cognitive-services/computer-vision/quickstarts/javascript)</span><span class="sxs-lookup"><span data-stu-id="90b1e-112">[Learn more](/azure/cognitive-services/computer-vision/home) about the Computer Vision API and get started with the [Computer Vision API JavaScript quickstart](/azure/cognitive-services/computer-vision/quickstarts/javascript).</span></span>

### <a name="content-moderator"></a><span data-ttu-id="90b1e-113">Content Moderator</span><span class="sxs-lookup"><span data-stu-id="90b1e-113">Content Moderator</span></span>

<span data-ttu-id="90b1e-114">Computergestützte Moderation von Texten, Videos und Bildern, erweitert um Tools für die Überprüfung durch Personen.</span><span class="sxs-lookup"><span data-stu-id="90b1e-114">Machine-assisted moderation of text, video and images, augmented with human review tools.</span></span>

<span data-ttu-id="90b1e-115">Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:</span><span class="sxs-lookup"><span data-stu-id="90b1e-115">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-contentmoderator
```

<span data-ttu-id="90b1e-116">[Weitere Informationen](/azure/cognitive-services/content-moderator/overview) zum Content Moderator-Dienst</span><span class="sxs-lookup"><span data-stu-id="90b1e-116">[Learn more](/azure/cognitive-services/content-moderator/overview) about the Content Moderator service.</span></span>

### <a name="face-api"></a><span data-ttu-id="90b1e-117">Gesichtserkennungs-API</span><span class="sxs-lookup"><span data-stu-id="90b1e-117">Face API</span></span>

<span data-ttu-id="90b1e-118">Nutzen Sie die Erkennung, Analyse, Organisation und Markierung von Gesichtern auf Fotos.</span><span class="sxs-lookup"><span data-stu-id="90b1e-118">Detect, identify, analyze, organize, and tag faces in photos.</span></span> 

<span data-ttu-id="90b1e-119">Testen Sie die [Gesichtserkennungs-API](https://azure.microsoft.com/services/cognitive-services/face/) in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="90b1e-119">[Try the Face API](https://azure.microsoft.com/services/cognitive-services/face/) in your browser.</span></span>

<span data-ttu-id="90b1e-120">Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:</span><span class="sxs-lookup"><span data-stu-id="90b1e-120">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-face
```

<span data-ttu-id="90b1e-121">[Weitere Informationen](/azure/cognitive-services/face/overview) zur Gesichtserkennungs-API und erste Schritte mit dem [Schnellstart für die Gesichtserkennungs-API mit JavaScript](/azure/cognitive-services/Face/quickstarts/javascript)</span><span class="sxs-lookup"><span data-stu-id="90b1e-121">[Learn more](/azure/cognitive-services/face/overview) about the Face API and get started with the [Face API JavaScript quickstart](/azure/cognitive-services/Face/quickstarts/javascript).</span></span>

## <a name="search-modules"></a><span data-ttu-id="90b1e-122">Suchmodule</span><span class="sxs-lookup"><span data-stu-id="90b1e-122">Search modules</span></span>

### <a name="web-search"></a><span data-ttu-id="90b1e-123">Websuche</span><span class="sxs-lookup"><span data-stu-id="90b1e-123">Web search</span></span>

<span data-ttu-id="90b1e-124">Rufen Sie durch die Bing-Websuche-API indizierte Webdokumente ab, und grenzen Sie die Ergebnisse anhand des Ergebnistyps, der Aktualität und anderer Faktoren ein.</span><span class="sxs-lookup"><span data-stu-id="90b1e-124">Retrieve web documents indexed by the Bing Web Search API and narrow down the results by result type, freshness and more.</span></span> 

<span data-ttu-id="90b1e-125">Testen Sie die [Websuche-API](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="90b1e-125">[Try the Web Search API](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) in your browser.</span></span>

<span data-ttu-id="90b1e-126">Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:</span><span class="sxs-lookup"><span data-stu-id="90b1e-126">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-websearch
```

<span data-ttu-id="90b1e-127">[Weitere Informationen](/azure/cognitive-services/bing-web-search/overview) zur Bing-Websuche-API und erste Schritte mit dem [Schnellstart für die Websuche-API mit Node.js](/azure/cognitive-services/bing-web-search/quickstarts/nodejs)</span><span class="sxs-lookup"><span data-stu-id="90b1e-127">[Learn more](/azure/cognitive-services/bing-web-search/overview) about the Bing Web Search API and get started with the [Web Search API Node.js quickstart](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).</span></span>

### <a name="image-search"></a><span data-ttu-id="90b1e-128">Bildersuche</span><span class="sxs-lookup"><span data-stu-id="90b1e-128">Image search</span></span>

<span data-ttu-id="90b1e-129">Suchen Sie nach Bildern, und erhalten Sie Ergebnisse mit Miniaturansichten, vollständigen URLs von Bildern, Bildmetadaten und vielem mehr.</span><span class="sxs-lookup"><span data-stu-id="90b1e-129">Search for images and get thumbnails, full image URLs, image metadata and more in your results.</span></span>

<span data-ttu-id="90b1e-130">Testen Sie die [Bildersuche-API](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="90b1e-130">[Try the Image Search API](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) in your browser.</span></span>

<span data-ttu-id="90b1e-131">Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:</span><span class="sxs-lookup"><span data-stu-id="90b1e-131">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-imagesearch
```

<span data-ttu-id="90b1e-132">[Weitere Informationen](/azure/cognitive-services/bing-image-search/overview) zur Bing-Bildersuche-API und erste Schritte mit dem [Schnellstart für die Bildersuche-API mit Node.js](/azure/cognitive-services/bing-image-search/quickstarts/nodejs)</span><span class="sxs-lookup"><span data-stu-id="90b1e-132">[Learn more](/azure/cognitive-services/bing-image-search/overview) about the Bing Image Search API and get started with the [Image Search API Node.js quickstart](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).</span></span>


### <a name="entity-search"></a><span data-ttu-id="90b1e-133">Entitätssuche</span><span class="sxs-lookup"><span data-stu-id="90b1e-133">Entity search</span></span>

<span data-ttu-id="90b1e-134">Suchen Sie nach der relevantesten Entität (Orte, Personen oder Dinge) für einen bestimmten Suchbegriff oder Ort.</span><span class="sxs-lookup"><span data-stu-id="90b1e-134">Search for the most relevant entity (place, person, or thing) for a given search term or location.</span></span>

<span data-ttu-id="90b1e-135">Testen Sie die [Entitätssuche-API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="90b1e-135">[Try the Entity Search API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) in your browser.</span></span>

<span data-ttu-id="90b1e-136">Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:</span><span class="sxs-lookup"><span data-stu-id="90b1e-136">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-entitysearch
```

<span data-ttu-id="90b1e-137">[Weitere Informationen](/azure/cognitive-services/bing-entities-search/search-the-web) zur Bing-Entitätssuche-API und erste Schritte mit dem [Schnellstart für die Entitätssuche-API mit Node.js](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs)</span><span class="sxs-lookup"><span data-stu-id="90b1e-137">[Learn more](/azure/cognitive-services/bing-entities-search/search-the-web) about the Bing Entity Search API and get started with the [Entity Search API Node.js quickstart](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).</span></span>

### <a name="custom-search"></a><span data-ttu-id="90b1e-138">Benutzerdefinierte Suche</span><span class="sxs-lookup"><span data-stu-id="90b1e-138">Custom search</span></span>

<span data-ttu-id="90b1e-139">Erstellen Sie eine benutzerdefinierte Websuche für Ihren spezifischen Suchbereich.</span><span class="sxs-lookup"><span data-stu-id="90b1e-139">Build and a custom web search that meets your specific search domain.</span></span>

<span data-ttu-id="90b1e-140">Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:</span><span class="sxs-lookup"><span data-stu-id="90b1e-140">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-customsearch
```

<span data-ttu-id="90b1e-141">[Weitere Informationen](/azure/cognitive-services/bing-custom-search/) zum Dienst für die benutzerdefinierte Bing-Suche und erste Schritte beim Abfragen der benutzerdefinierten Suche für Ihre Apps mit dem [Schnellstart für die API für die benutzerdefinierte Suche mit Node.js](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs)</span><span class="sxs-lookup"><span data-stu-id="90b1e-141">[Learn more](/azure/cognitive-services/bing-custom-search/) about the Bing Custom Search service and get started with querying your custom search from your apps with the [Custom Search API Node.js quickstart](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).</span></span>

### <a name="video-search"></a><span data-ttu-id="90b1e-142">Videosuche</span><span class="sxs-lookup"><span data-stu-id="90b1e-142">Video search</span></span>

<span data-ttu-id="90b1e-143">Finden Sie Videos überall im Web, und erhalten Sie Ergebnisse mit Metadaten wie Ersteller, Codierungsformat, Länge und Aufrufe.</span><span class="sxs-lookup"><span data-stu-id="90b1e-143">Find videos across the web and get results with creator, encoding, length, and view count metadata.</span></span>

<span data-ttu-id="90b1e-144">Testen Sie die [Videosuche-API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="90b1e-144">[Try the Video Search API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) in your browser.</span></span>

<span data-ttu-id="90b1e-145">Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:</span><span class="sxs-lookup"><span data-stu-id="90b1e-145">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-videosearch
```

<span data-ttu-id="90b1e-146">[Weitere Informationen](/azure/cognitive-services/bing-video-search/search-the-web) zum Bing-Videosuchdienst und erste Schritte mit dem [Schnellstart für die Videosuche-API mit Node.js](/azure/cognitive-services/bing-video-search/nodejs)</span><span class="sxs-lookup"><span data-stu-id="90b1e-146">[Learn more](/azure/cognitive-services/bing-video-search/search-the-web) about the Bing Video Search service and get started with the [Video Search API Node.js quickstart](/azure/cognitive-services/bing-video-search/nodejs).</span></span>


### <a name="news-search"></a><span data-ttu-id="90b1e-147">News-Suche</span><span class="sxs-lookup"><span data-stu-id="90b1e-147">News search</span></span>

<span data-ttu-id="90b1e-148">Durchsuchen Sie das Web nach Nachrichtenartikeln, und nutzen Sie Metadaten zu Artikeln, zugehörigen News, Bildern und Informationen zur Quelle.</span><span class="sxs-lookup"><span data-stu-id="90b1e-148">Search the web for news articles and work with article, related news, images, and provider info metadata.</span></span>

<span data-ttu-id="90b1e-149">Testen Sie die [News-Suche-API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="90b1e-149">[Try the News Search API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) in your browser.</span></span>

<span data-ttu-id="90b1e-150">Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:</span><span class="sxs-lookup"><span data-stu-id="90b1e-150">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-newssearch
```

<span data-ttu-id="90b1e-151">[Weitere Informationen](/azure/cognitive-services/bing-news-search/search-the-web) zum Bing-Dienst für die News-Suche und erste Schritte mit dem [Schnellstart für die News-Suche-API mit JavaScript](/azure/cognitive-services/bing-news-search/nodejs)</span><span class="sxs-lookup"><span data-stu-id="90b1e-151">[Learn more](/azure/cognitive-services/bing-news-search/search-the-web) about the Bing News Search service and get started with the [News Search API JavaScript quickstart](/azure/cognitive-services/bing-news-search/nodejs).</span></span>


## <a name="language-modules"></a><span data-ttu-id="90b1e-152">Sprachmodule</span><span class="sxs-lookup"><span data-stu-id="90b1e-152">Language modules</span></span>

### <a name="text-analytics"></a><span data-ttu-id="90b1e-153">Textanalyse</span><span class="sxs-lookup"><span data-stu-id="90b1e-153">Text Analytics</span></span> 

<span data-ttu-id="90b1e-154">Die Textanalyse-API ist ein cloudbasierter Dienst für die Verarbeitung natürlicher Sprache aus unformatiertem Text.</span><span class="sxs-lookup"><span data-stu-id="90b1e-154">The Text Analytics API is a cloud-based service that provides  natural language processing over raw text.</span></span> <span data-ttu-id="90b1e-155">Die API bietet drei Hauptfunktionen:</span><span class="sxs-lookup"><span data-stu-id="90b1e-155">The API includes three main functions:</span></span>

- <span data-ttu-id="90b1e-156">Stimmungsanalyse</span><span class="sxs-lookup"><span data-stu-id="90b1e-156">Sentiment analysis</span></span>
- <span data-ttu-id="90b1e-157">Schlüsselwortextraktion</span><span class="sxs-lookup"><span data-stu-id="90b1e-157">Key phrase extraction</span></span>
- <span data-ttu-id="90b1e-158">Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="90b1e-158">Language detection</span></span>

<span data-ttu-id="90b1e-159">Testen Sie die [Textanalyse-API](https://azure.microsoft.com/services/cognitive-services/text-analytics/) in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="90b1e-159">[Try the Text Analytics API](https://azure.microsoft.com/services/cognitive-services/text-analytics/) in your browser.</span></span>

<span data-ttu-id="90b1e-160">Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:</span><span class="sxs-lookup"><span data-stu-id="90b1e-160">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-textanalytics
```

<span data-ttu-id="90b1e-161">[Weitere Informationen](/azure/cognitive-services/text-analytics/overview) zur Textanalyse-API und erste Schritte mit dem [Schnellstart für die Textanalyse-API mit Node.js](/azure/cognitive-services/text-analytics/quickstarts/nodejs)</span><span class="sxs-lookup"><span data-stu-id="90b1e-161">[Learn more](/azure/cognitive-services/text-analytics/overview) about the Text Analytics API and get started with the [Text Analytics API Node.js quickstart](/azure/cognitive-services/text-analytics/quickstarts/nodejs).</span></span>


### <a name="spell-check"></a><span data-ttu-id="90b1e-162">Rechtschreibprüfung</span><span class="sxs-lookup"><span data-stu-id="90b1e-162">Spell Check</span></span>

<span data-ttu-id="90b1e-163">Überprüfen Sie mit der Bing-Rechtschreibprüfungs-API Grammatik und Rechtschreibung im Kontext.</span><span class="sxs-lookup"><span data-stu-id="90b1e-163">Perform contextual grammar and spell checking with the Bing Spell Check API.</span></span>

<span data-ttu-id="90b1e-164">Testen Sie die [Rechtschreibprüfungs-API](https://azure.microsoft.com/services/cognitive-services/spell-check/) in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="90b1e-164">[Try the Spell Check API](https://azure.microsoft.com/services/cognitive-services/spell-check/) in your browser.</span></span>

<span data-ttu-id="90b1e-165">Rufen Sie das JavaScript-Modul mit [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) ab:</span><span class="sxs-lookup"><span data-stu-id="90b1e-165">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-spellcheck
```

<span data-ttu-id="90b1e-166">[Weitere Informationen](/azure/cognitive-services/bing-spell-check/proof-text) zur Rechtschreibprüfungs-API und erste Schritte mit dem [Schnellstart für die Rechtschreibprüfungs-API mit Node.js](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs)</span><span class="sxs-lookup"><span data-stu-id="90b1e-166">[Learn more](/azure/cognitive-services/bing-spell-check/proof-text) about the Spell Check API and get started with the [Spell Check API Node.js quickstart](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).</span></span>

## <a name="samples"></a><span data-ttu-id="90b1e-167">Beispiele</span><span class="sxs-lookup"><span data-stu-id="90b1e-167">Samples</span></span>

<span data-ttu-id="90b1e-168">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="90b1e-168">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
