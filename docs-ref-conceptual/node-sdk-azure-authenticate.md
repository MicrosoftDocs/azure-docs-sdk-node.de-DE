---
title: Authentifizieren mit den Azure-Verwaltungsmodulen für Node.js
description: Authentifizieren mit einem Dienstprinzipal bei den Azure-Verwaltungsmodulen für Node.js
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: b665c537bf17d08c44357009552054d6b2e609d2
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a>Authentifizieren mit den Azure-Modulen für Node.js 

Für alle Dienst-APIs ist bei der Instanziierung die Authentifizierung mit einem `credentials`-Objekt erforderlich. Es gibt drei Möglichkeiten, die erforderlichen Anmeldeinformationen über das Azure SDK für Node.js zu authentifizieren und zu erstellen: 

- Standardauthentifizierung
- Interaktive Anmeldung
- Dienstprinzipalauthentifizierung

## <a name="basic-authentication"></a>Standardauthentifizierung

Verwenden Sie die Funktion `loginWithUsernamePassword`, um die programmgesteuerte Authentifizierung mit den Anmeldeinformationen für Ihr Azure-Konto durchzuführen. Der folgende JavaScript-Codeausschnitt veranschaulicht, wie Sie die einfache Authentifizierung mit Anmeldeinformationen nutzen, die als Umgebungsvariablen gespeichert sind. 

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithUsernamePassword(process.env.AZURE_USER, 
                                 process.env.AZURE_PASS, 
                                 (err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, 
                                                             '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="interactive-login"></a>Interaktive Anmeldung

Bei der interaktiven Anmeldung werden ein Link und ein Code bereitgestellt, und mit diesen Angaben können sich Benutzer über einen Browser authentifizieren. Nutzen Sie diese Methode, wenn von demselben Skript mehrere Konten verwendet werden oder wenn der Benutzereingriff gewünscht ist.

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a>Dienstprinzipalauthentifizierung

Die [interaktive Anmeldung](#interactive-login) ist die einfachste Möglichkeit, die Authentifizierung durchzuführen. Bei der Verwendung des Node.js SDK kann es dagegen ratsam sein, die Dienstprinzipalauthentifizierung zu nutzen, anstatt die Anmeldeinformationen für Ihr Konto anzugeben. Im Thema [Erstellen eines Azure-Dienstprinzipals mit Node.js](./node-sdk-azure-authenticate-principal.md) werden verschiedene Techniken zum Erstellen (und Verwenden) eines Dienstprinzipals beschrieben. 