---
title: Azure Relay-Module für Node.js
description: Referenz zu Azure Relay-Modulen für Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: 1f9b4263b8ffae78fcf9f35b8ef0160095059693
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260783"
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="da36b-103">Azure Relay-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="da36b-103">Azure Relay modules for Node.js</span></span>

<span data-ttu-id="da36b-104">Der Azure Relay-Dienst erstellt Hybridanwendungen, indem er Ihnen die Möglichkeit bietet, WCF-Dienste in einem Unternehmensnetzwerk sicher in der öffentlichen Cloud bereitzustellen, ohne dass eine Firewallverbindung geöffnet werden muss oder tiefgreifende Änderungen an der unternehmensinternen Netzwerkinfrastruktur erforderlich werden.</span><span class="sxs-lookup"><span data-stu-id="da36b-104">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="da36b-105">Relay unterstützt eine Vielzahl verschiedener Transportprotokolle und Webdienststandards.</span><span class="sxs-lookup"><span data-stu-id="da36b-105">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="da36b-106">Weitere Informationen zu [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="da36b-106">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="da36b-107">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="da36b-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="da36b-108">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="da36b-108">Install the npm module</span></span>

<span data-ttu-id="da36b-109">Installieren des npm-Moduls für Azure Relay</span><span class="sxs-lookup"><span data-stu-id="da36b-109">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="da36b-110">Beispiel</span><span class="sxs-lookup"><span data-stu-id="da36b-110">Example</span></span>

<span data-ttu-id="da36b-111">Mit diesem Beispiel werden die Namespaces für einen Relay-Client aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="da36b-111">This example lists the namespaces for a Relay client.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RelayManagement = require('azure-arm-relay');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RelayManagement(credentials, subscriptionId);
    return client.namespaces.list();
  })
  .then(namespaces => {
    console.dir(namespaces, { depth: null, colors: true });
  })
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="da36b-112">Beispiele</span><span class="sxs-lookup"><span data-stu-id="da36b-112">Samples</span></span>

<span data-ttu-id="da36b-113">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="da36b-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
