---
title: Cognitive Services Speech SDK für JavaScript
description: Referenz zum Cognitive Services Speech SDK für JavaScript
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 12/18/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.subservice: speech-service
ms.openlocfilehash: b1375b6beb478cab2475539c03b6bac9f0ea99e0
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052579"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>Cognitive Services Speech SDK für JavaScript

## <a name="overview"></a>Übersicht

Um die Entwicklung sprachaktivierter Anwendungen zu vereinfachen, stellt Microsoft das Speech SDK für den [Speech-Dienst](https://aka.ms/csspeech) bereit.
Das Speech SDK bietet konsistente native Spracherkennungs- und Sprachübersetzungs-APIs.

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls des Cognitive Services Speech SDK

```bash
npm install microsoft-cognitiveservices-speech-sdk
```

### <a name="example"></a>Beispiel 

Die folgenden Codeausschnitte veranschaulichen, wie die einfache Spracherkennung in einer Datei funktioniert:

```javascript 
// Pull in the required packages.
var sdk = require("microsoft-cognitiveservices-speech-sdk");
var fs = require("fs");

// Replace with your own subscription key, service region (e.g., "westus"), and
// the name of the file you want to run through the speech recognizer.
var subscriptionKey = "YourSubscriptionKey";
var serviceRegion = "YourServiceRegion"; // e.g., "westus"
var filename = "YourAudioFile.wav"; // 16000 Hz, Mono

// Create the push stream we need for the speech sdk.
var pushStream = sdk.AudioInputStream.createPushStream();

// Open the file and push it to the push stream.
fs.createReadStream(filename).on('data', function(arrayBuffer) {
  pushStream.write(arrayBuffer.buffer);
}).on('end', function() {
  pushStream.close();
});

// We are done with the setup
console.log("Now recognizing from: " + filename);

// Create the audio-config pointing to our stream and
// the speech config specifying the language.
var audioConfig = sdk.AudioConfig.fromStreamInput(pushStream);
var speechConfig = sdk.SpeechConfig.fromSubscription(subscriptionKey, serviceRegion);

// Setting the recognition language to English.
speechConfig.speechRecognitionLanguage = "en-US";

// Create the speech recognizer.
var recognizer = new sdk.SpeechRecognizer(speechConfig, audioConfig);

// Start the recognizer and wait for a result.
recognizer.recognizeOnceAsync(
  function (result) {
    console.log(result);

    recognizer.close();
    recognizer = undefined;
  },
  function (err) {
    console.trace("err - " + err);

    recognizer.close();
    recognizer = undefined;
  });
``` 

Sehen Sie sich unsere [ausführlichen Schnellstartanleitungen](/azure/cognitive-services/speech-service/quickstart-js-node) an.

## <a name="samples"></a>Beispiele

* [Schnellstart: Erkennen von Sprache in JavaScript in Node.js mit dem Speech Service SDK](/azure/cognitive-services/speech-service/quickstart-js-node)
* [Schnellstart: Erkennen von Sprache in JavaScript in einem Browser mit dem Speech Service SDK](/azure/cognitive-services/speech-service/quickstart-js-browser)
* Weitere Beispiele finden Sie im [Speech SDK-Beispielrepository](https://aka.ms/csspeech/samples).
