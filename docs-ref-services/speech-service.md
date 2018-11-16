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
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51487905"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>Cognitive Services Speech SDK für JavaScript

## <a name="overview"></a>Übersicht

Um die Entwicklung sprachaktivierter Anwendungen zu vereinfachen, stellt Microsoft das Speech SDK für den [Speech-Dienst](https://aka.ms/csspeech) bereit.
Das Speech SDK bietet konsistente native Spracherkennungs- und Sprachübersetzungs-APIs.

> [!NOTE]
> Das Cognitive Services Speech SDK ist derzeit nur für Browser verfügbar.
> Ein NPM-Paket folgt in Kürze.

### <a name="install-the-speech-sdk"></a>Installieren des Speech SDK

Laden Sie das Speech SDK als [ZIP-Paket](https://aka.ms/csspeech/jsbrowserpackage) herunter, und entpacken Sie es.
Daraufhin sollte eine Reihe von Dateien, einschließlich einer Datei mit dem Namen `microsoft.cognitiveservices.speech.sdk.bundle.js`, entpackt werden.
Laden Sie diese Datei als Skriptressource in Ihre Webseite, um das Speech SDK zu verwenden:

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a>Beispiel 

Die folgenden Codeausschnitte veranschaulichen, wie die einfache Spracherkennung in Ihrem Browser funktioniert:

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

Sehen Sie sich unsere [ausführlichen Schnellstartanleitungen](/azure/cognitive-services/speech-service/quickstart-js-browser) an.

## <a name="samples"></a>Beispiele

Sehen Sie sich im [Speech SDK-Beispielrepository](https://aka.ms/csspeech/samples) weitere Beispiele an.
