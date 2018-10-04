---
title: Cognitive Services Speech SDK für JavaScript
description: Referenz zum Cognitive Services Speech SDK für JavaScript
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 09/24/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.component: speech-service
ms.openlocfilehash: 69167faa5b2677fc15561ed33beccf7925efbe39
ms.sourcegitcommit: 8f2555cd23e454ff79e27bd3ed0a6f65b08c1c9e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "48458648"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="8c37c-103">Cognitive Services Speech SDK für JavaScript</span><span class="sxs-lookup"><span data-stu-id="8c37c-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="8c37c-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="8c37c-104">Overview</span></span>

<span data-ttu-id="8c37c-105">Um die Entwicklung sprachaktivierter Anwendungen zu vereinfachen, stellt Microsoft das Speech SDK für den [Speech-Dienst](https://aka.ms/csspeech) bereit.</span><span class="sxs-lookup"><span data-stu-id="8c37c-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="8c37c-106">Das Speech SDK bietet konsistente native Spracherkennungs- und Sprachübersetzungs-APIs.</span><span class="sxs-lookup"><span data-stu-id="8c37c-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="8c37c-107">Das Cognitive Services Speech SDK ist derzeit nur für Browser verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8c37c-107">The Cognitive Services Speech SDK is currently available only for browsers.</span></span>
> <span data-ttu-id="8c37c-108">Ein NPM-Paket folgt in Kürze.</span><span class="sxs-lookup"><span data-stu-id="8c37c-108">An NPM package will follow soon.</span></span>

### <a name="install-the-speech-sdk"></a><span data-ttu-id="8c37c-109">Installieren des Speech SDK</span><span class="sxs-lookup"><span data-stu-id="8c37c-109">Install the Speech SDK</span></span>

<span data-ttu-id="8c37c-110">Laden Sie das Speech SDK als [ZIP-Paket](https://aka.ms/csspeech/jsbrowserpackage) herunter, und entpacken Sie es.</span><span class="sxs-lookup"><span data-stu-id="8c37c-110">Download the Speech SDK as a [.zip package](https://aka.ms/csspeech/jsbrowserpackage) and unpack it.</span></span>
<span data-ttu-id="8c37c-111">Daraufhin sollte eine Reihe von Dateien, einschließlich einer Datei mit dem Namen `microsoft.cognitiveservices.speech.sdk.bundle.js`, entpackt werden.</span><span class="sxs-lookup"><span data-stu-id="8c37c-111">This should result in a number of files being unpacked including a file named `microsoft.cognitiveservices.speech.sdk.bundle.js`.</span></span>
<span data-ttu-id="8c37c-112">Laden Sie diese Datei als Skriptressource in Ihre Webseite, um das Speech SDK zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="8c37c-112">Load this file as a script resource in your web page to start using the Speech SDK:</span></span>

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a><span data-ttu-id="8c37c-113">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8c37c-113">Example</span></span> 

<span data-ttu-id="8c37c-114">Die folgenden Codeausschnitte veranschaulichen, wie die einfache Spracherkennung in Ihrem Browser funktioniert:</span><span class="sxs-lookup"><span data-stu-id="8c37c-114">The following code snippets illustrates how to do simple speech recognition from your browser:</span></span>

```javascript 
var SpeechSDK = window.SpeechSDK;
var speechConfig = SpeechSDK.SpeechConfig.fromSubscription("your-subscription-key", "your-service-region");
speechConfig.language = "en-US";
var audioConfig = SpeechSDK.AudioConfig.fromDefaultMicrophoneInput();
recognizer = new SpeechSDK.SpeechRecognizer(speechConfig, audioConfig);

recognizer.recognizeOnceAsync(
  function (result) {
    alert("Recognition result:" + JSON.stringify(result));
    recognizer.close();
  },
  function (err) {
    alert("An error occurred:" + JSON.stringify(err));
    recognizer.close();
  }
);
``` 

<span data-ttu-id="8c37c-115">Sehen Sie sich unsere [ausführlichen Schnellstartanleitungen](/azure/cognitive-services/speech-service/quickstart-js-browser) an.</span><span class="sxs-lookup"><span data-stu-id="8c37c-115">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>

## <a name="samples"></a><span data-ttu-id="8c37c-116">Beispiele</span><span class="sxs-lookup"><span data-stu-id="8c37c-116">Samples</span></span>

<span data-ttu-id="8c37c-117">Sehen Sie sich im [Speech SDK-Beispielrepository](https://aka.ms/csspeech/samples) weitere Beispiele an.</span><span class="sxs-lookup"><span data-stu-id="8c37c-117">Explore more samples in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
