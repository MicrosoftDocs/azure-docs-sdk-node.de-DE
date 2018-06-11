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
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a>Microsoft Azure SDK für Node.js: ContainerServiceClient
Dieses Projekt enthält ein Node.js-Paket für den Zugriff auf Azure. Momentan werden folgende Versionen unterstützt:
- **Node.js, Version 6.x.x oder höher**

## <a name="features"></a>Features


## <a name="how-to-install"></a>Installation

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a>Verwendung

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a>Authentifizierung, Clienterstellung und Auflisten von „containerServices“ als Beispiel

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

## <a name="related-projects"></a>Verwandte Projekte

- [Microsoft Azure SDK für Node.js](https://github.com/Azure/azure-sdk-for-node)