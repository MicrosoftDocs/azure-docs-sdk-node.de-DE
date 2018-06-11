---
title: Azure Container Service-Module für Node.js
description: Referenz zu Azure Container Service-Modulen für Node.js
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Service
ms.openlocfilehash: 2d0aac2f7f6cc70ab3e40f7b3ccee6f64a011b55
ms.sourcegitcommit: 702a716434eb42f55d8782feb62ae2c6d8147aa9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34689826"
---
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a><span data-ttu-id="da24e-103">Microsoft Azure SDK für Node.js: ContainerServiceClient</span><span class="sxs-lookup"><span data-stu-id="da24e-103">Microsoft Azure SDK for Node.js - ContainerServiceClient</span></span>
<span data-ttu-id="da24e-104">Dieses Projekt enthält ein Node.js-Paket für den Zugriff auf Azure.</span><span class="sxs-lookup"><span data-stu-id="da24e-104">This project provides a Node.js package for accessing Azure.</span></span> <span data-ttu-id="da24e-105">Momentan werden folgende Versionen unterstützt:</span><span class="sxs-lookup"><span data-stu-id="da24e-105">Right now it supports:</span></span>
- <span data-ttu-id="da24e-106">**Node.js, Version 6.x.x oder höher**</span><span class="sxs-lookup"><span data-stu-id="da24e-106">**Node.js version 6.x.x or higher**</span></span>

## <a name="features"></a><span data-ttu-id="da24e-107">Features</span><span class="sxs-lookup"><span data-stu-id="da24e-107">Features</span></span>


## <a name="how-to-install"></a><span data-ttu-id="da24e-108">Installation</span><span class="sxs-lookup"><span data-stu-id="da24e-108">How to Install</span></span>

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a><span data-ttu-id="da24e-109">Verwendung</span><span class="sxs-lookup"><span data-stu-id="da24e-109">How to use</span></span>

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a><span data-ttu-id="da24e-110">Authentifizierung, Clienterstellung und Auflisten von „containerServices“ als Beispiel</span><span class="sxs-lookup"><span data-stu-id="da24e-110">Authentication, client creation and list containerServices as an example.</span></span>

```javascript
const msRestAzure = require("ms-rest-azure");
const ContainerServiceClient = require("azure-arm-containerservice");
msRestAzure.interactiveLogin().then((creds) => {
    const subscriptionId = "<Subscription_Id>";
    const client = new ContainerServiceClient(creds, subscriptionId);
    return client.containerServices.list().then((result) => {
      console.log("The result is:");
      console.log(result);
    });
}).catch((err) => {
  console.log('An error ocurred:');
  console.dir(err, {depth: null, colors: true});
});
```

## <a name="related-projects"></a><span data-ttu-id="da24e-111">Verwandte Projekte</span><span class="sxs-lookup"><span data-stu-id="da24e-111">Related projects</span></span>

- [<span data-ttu-id="da24e-112">Microsoft Azure SDK für Node.js</span><span class="sxs-lookup"><span data-stu-id="da24e-112">Microsoft Azure SDK for Node.js</span></span>](https://github.com/Azure/azure-sdk-for-node)