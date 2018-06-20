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
ms.locfileid: "34220512"
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="3d7ea-103">Authentifizieren mit den Azure-Modulen für Node.js</span><span class="sxs-lookup"><span data-stu-id="3d7ea-103">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="3d7ea-104">Für alle Dienst-APIs ist bei der Instanziierung die Authentifizierung mit einem `credentials`-Objekt erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3d7ea-104">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="3d7ea-105">Es gibt drei Möglichkeiten, die erforderlichen Anmeldeinformationen über das Azure SDK für Node.js zu authentifizieren und zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="3d7ea-105">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="3d7ea-106">Standardauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="3d7ea-106">Basic authentication</span></span>
- <span data-ttu-id="3d7ea-107">Interaktive Anmeldung</span><span class="sxs-lookup"><span data-stu-id="3d7ea-107">Interactive login</span></span>
- <span data-ttu-id="3d7ea-108">Dienstprinzipalauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="3d7ea-108">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="3d7ea-109">Standardauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="3d7ea-109">Basic authentication</span></span>

<span data-ttu-id="3d7ea-110">Verwenden Sie die Funktion `loginWithUsernamePassword`, um die programmgesteuerte Authentifizierung mit den Anmeldeinformationen für Ihr Azure-Konto durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="3d7ea-110">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="3d7ea-111">Der folgende JavaScript-Codeausschnitt veranschaulicht, wie Sie die einfache Authentifizierung mit Anmeldeinformationen nutzen, die als Umgebungsvariablen gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="3d7ea-111">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

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

## <a name="interactive-login"></a><span data-ttu-id="3d7ea-112">Interaktive Anmeldung</span><span class="sxs-lookup"><span data-stu-id="3d7ea-112">Interactive login</span></span>

<span data-ttu-id="3d7ea-113">Bei der interaktiven Anmeldung werden ein Link und ein Code bereitgestellt, und mit diesen Angaben können sich Benutzer über einen Browser authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="3d7ea-113">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="3d7ea-114">Nutzen Sie diese Methode, wenn von demselben Skript mehrere Konten verwendet werden oder wenn der Benutzereingriff gewünscht ist.</span><span class="sxs-lookup"><span data-stu-id="3d7ea-114">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="3d7ea-115">Dienstprinzipalauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="3d7ea-115">Service principal authentication</span></span>

<span data-ttu-id="3d7ea-116">Die [interaktive Anmeldung](#interactive-login) ist die einfachste Möglichkeit, die Authentifizierung durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="3d7ea-116">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="3d7ea-117">Bei der Verwendung des Node.js SDK kann es dagegen ratsam sein, die Dienstprinzipalauthentifizierung zu nutzen, anstatt die Anmeldeinformationen für Ihr Konto anzugeben.</span><span class="sxs-lookup"><span data-stu-id="3d7ea-117">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="3d7ea-118">Im Thema [Erstellen eines Azure-Dienstprinzipals mit Node.js](./node-sdk-azure-authenticate-principal.md) werden verschiedene Techniken zum Erstellen (und Verwenden) eines Dienstprinzipals beschrieben.</span><span class="sxs-lookup"><span data-stu-id="3d7ea-118">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 