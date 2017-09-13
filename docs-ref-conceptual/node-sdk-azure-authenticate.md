---
title: "Authentifizieren mit den Azure-Verwaltungsmodulen für Node.js"
description: "Authentifizieren mit einem Dienstprinzipal bei den Azure-Verwaltungsmodulen für Node.js"
keywords: Azure, Node, SDK, API, Authentifizierung, Active Directory, Dienstprinzipal
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 3ad1f17435844852838d01115ad8326f141aa73c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="42c9c-104">Authentifizieren mit den Azure-Modulen für Node.js</span><span class="sxs-lookup"><span data-stu-id="42c9c-104">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="42c9c-105">Für alle Dienst-APIs ist bei der Instanziierung die Authentifizierung mit einem `credentials`-Objekt erforderlich.</span><span class="sxs-lookup"><span data-stu-id="42c9c-105">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="42c9c-106">Es gibt drei Möglichkeiten, die erforderlichen Anmeldeinformationen über das Azure SDK für Node.js zu authentifizieren und zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="42c9c-106">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="42c9c-107">Standardauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="42c9c-107">Basic authentication</span></span>
- <span data-ttu-id="42c9c-108">Interaktive Anmeldung</span><span class="sxs-lookup"><span data-stu-id="42c9c-108">Interactive login</span></span>
- <span data-ttu-id="42c9c-109">Dienstprinzipalauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="42c9c-109">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="42c9c-110">Standardauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="42c9c-110">Basic authentication</span></span>

<span data-ttu-id="42c9c-111">Verwenden Sie die Funktion `loginWithUsernamePassword`, um die programmgesteuerte Authentifizierung mit den Anmeldeinformationen für Ihr Azure-Konto durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="42c9c-111">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="42c9c-112">Der folgende JavaScript-Codeausschnitt veranschaulicht, wie Sie die einfache Authentifizierung mit Anmeldeinformationen nutzen, die als Umgebungsvariablen gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="42c9c-112">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

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

## <a name="interactive-login"></a><span data-ttu-id="42c9c-113">Interaktive Anmeldung</span><span class="sxs-lookup"><span data-stu-id="42c9c-113">Interactive login</span></span>

<span data-ttu-id="42c9c-114">Bei der interaktiven Anmeldung werden ein Link und ein Code bereitgestellt, und mit diesen Angaben können sich Benutzer über einen Browser authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="42c9c-114">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="42c9c-115">Nutzen Sie diese Methode, wenn von demselben Skript mehrere Konten verwendet werden oder wenn der Benutzereingriff gewünscht ist.</span><span class="sxs-lookup"><span data-stu-id="42c9c-115">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="42c9c-116">Dienstprinzipalauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="42c9c-116">Service principal authentication</span></span>

<span data-ttu-id="42c9c-117">Die [interaktive Anmeldung](#interactive-login) ist die einfachste Möglichkeit, die Authentifizierung durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="42c9c-117">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="42c9c-118">Bei der Verwendung des Node.js SDK kann es dagegen ratsam sein, die Dienstprinzipalauthentifizierung zu nutzen, anstatt die Anmeldeinformationen für Ihr Konto anzugeben.</span><span class="sxs-lookup"><span data-stu-id="42c9c-118">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="42c9c-119">Im Thema [Erstellen eines Azure-Dienstprinzipals mit Node.js](./node-sdk-azure-authenticate-principal.md) werden verschiedene Techniken zum Erstellen (und Verwenden) eines Dienstprinzipals beschrieben.</span><span class="sxs-lookup"><span data-stu-id="42c9c-119">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 