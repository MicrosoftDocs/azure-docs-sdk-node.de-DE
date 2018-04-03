---
title: Azure Cosmos DB-Module für Node.js
description: Referenz zu Azure Cosmos DB-Modulen für Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 03/20/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 02d4729d72cba8628ac98de0bf41c30f54c75e85
ms.sourcegitcommit: 178734fbd3784ade4d8bdb5141be6d7ca7e017f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/23/2018
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="816e8-103">Azure Cosmos DB-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="816e8-103">Azure Cosmos DB Modules for Node.js</span></span>

<span data-ttu-id="816e8-104">Azure Cosmos DB ist eine global verteilte Datenbank von Microsoft mit mehreren Modellen.</span><span class="sxs-lookup"><span data-stu-id="816e8-104">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="816e8-105">Azure Cosmos DB ermöglicht es Ihnen, Durchsatz und Speicher elastisch und unabhängig voneinander über eine beliebige Anzahl von geografischen Azure-Regionen hinweg zu skalieren.</span><span class="sxs-lookup"><span data-stu-id="816e8-105">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="816e8-106">Azure Cosmos DB bietet Ihnen mit umfassenden Vereinbarungen zum Servicelevel (Service Level Agreements, SLAs) Durchsatz-, Wartezeit-, Verfügbarkeits- und Konsistenzgarantien wie kein anderer Datenbankdienst.</span><span class="sxs-lookup"><span data-stu-id="816e8-106">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="816e8-107">Azure Cosmos DB umfasst eine ressourcengesteuerte, vom Schema unabhängige Datenbank-Engine mit optimierten Schreibvorgängen, die mehrere Datenmodelle nativ unterstützt: Schlüssel-Wert-, Dokumenten-, Graph- und spaltenbasierte Datenmodelle.</span><span class="sxs-lookup"><span data-stu-id="816e8-107">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="816e8-108">Azure Cosmos DB unterstützt zudem viele APIs für den Zugriff auf Daten, z.B. MongoDB, SQL, Gremlin/Graph, Azure Tables und Cassandra (Vorschauversion) und ist erweiterbar.</span><span class="sxs-lookup"><span data-stu-id="816e8-108">It also supports many APIs for accessing data including MongoDB, SQL, Gremlin/Graph, Azure Tables, and Cassandra (preview) in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="816e8-109">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="816e8-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="816e8-110">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="816e8-110">Install the npm module</span></span> 

<span data-ttu-id="816e8-111">Installieren Sie das npm-Modul für Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="816e8-111">Install the Azure Cosmos DB npm module.</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="816e8-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="816e8-112">Example</span></span>

<span data-ttu-id="816e8-113">Mit diesem Beispiel werden alle Azure Cosmos DB-Konten aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="816e8-113">This example lists all Azure Cosmos DB accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const documentDBManagementClient = require('azure-arm-documentdb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const documentDbClient = new documentDBManagementClient(credentials, subscriptionId);
  documentDbClient.databaseAccounts
    .list()
    .then(databaseAccounts => console.log('Retrieved database accounts: ', databaseAccounts));
});
```

## <a name="samples"></a><span data-ttu-id="816e8-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="816e8-114">Samples</span></span>

* [<span data-ttu-id="816e8-115">Entwickeln einer Node.js-App mit Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="816e8-115">Developing a Node.js app using Azure Cosmos DB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="816e8-116">Entwickeln einer Node.js-App mit Azure Cosmos DB – Gremlin</span><span class="sxs-lookup"><span data-stu-id="816e8-116">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="816e8-117">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="816e8-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
