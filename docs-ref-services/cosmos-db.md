---
title: "Azure Cosmos DB-Module für Node.js"
description: "Referenz zu Azure Cosmos DB-Modulen für Node.js"
keywords: Azure,SDK,API,Cosmos DB, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 1f545f89b5304b611dbe1ed9cb86052c112f13c1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="afe03-104">Azure Cosmos DB-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="afe03-104">Azure Cosmos DB Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="afe03-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="afe03-105">Overview</span></span>

<span data-ttu-id="afe03-106">Azure Cosmos DB ist eine global verteilte Datenbank von Microsoft mit mehreren Modellen.</span><span class="sxs-lookup"><span data-stu-id="afe03-106">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="afe03-107">Azure Cosmos DB ermöglicht es Ihnen, Durchsatz und Speicher elastisch und unabhängig voneinander über eine beliebige Anzahl von geografischen Azure-Regionen hinweg zu skalieren.</span><span class="sxs-lookup"><span data-stu-id="afe03-107">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="afe03-108">Azure Cosmos DB bietet Ihnen mit umfassenden Vereinbarungen zum Servicelevel (Service Level Agreements, SLAs) Durchsatz-, Wartezeit-, Verfügbarkeits- und Konsistenzgarantien wie kein anderer Datenbankdienst.</span><span class="sxs-lookup"><span data-stu-id="afe03-108">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="afe03-109">Azure Cosmos DB enthält ein ressourcengesteuertes, vom Schema unabhängiges Datenbankmodul mit optimierten Schreibvorgängen, die mehrere Datenmodelle nativ unterstützt: Schlüssel-Wert-, Dokumenten-, Graph- und spaltenbasierte Datenmodelle.</span><span class="sxs-lookup"><span data-stu-id="afe03-109">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="afe03-110">Azure Cosmos DB unterstützt zudem viele APIs für den Zugriff auf Daten, z.B. MongoDB, DocumentDB SQL, Gremlin (Vorschauversion) und Azure-Tabellen (Vorschauversion), und ist erweiterbar.</span><span class="sxs-lookup"><span data-stu-id="afe03-110">It also supports many APIs for accessing data including MongoDB, DocumentDB SQL, Gremlin (preview), and Azure Tables (preview), in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="afe03-111">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="afe03-111">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="afe03-112">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="afe03-112">Install the npm module</span></span> 

<span data-ttu-id="afe03-113">Installieren des npm-Moduls für Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="afe03-113">Install the Azure Cosmos DB npm module</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="afe03-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="afe03-114">Example</span></span>

<span data-ttu-id="afe03-115">Mit diesem Beispiel werden alle Cosmos DB-Konten aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="afe03-115">This example lists all Cosmos DB accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="afe03-116">Beispiele</span><span class="sxs-lookup"><span data-stu-id="afe03-116">Samples</span></span>

* [<span data-ttu-id="afe03-117">Entwickeln einer Node.js-App mit Azure Cosmos DB – DocumentDB</span><span class="sxs-lookup"><span data-stu-id="afe03-117">Developing a Node.js app using Azure Cosmos DB - DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="afe03-118">Entwickeln einer Node.js-App mit Azure Cosmos DB – Gremlin</span><span class="sxs-lookup"><span data-stu-id="afe03-118">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="afe03-119">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="afe03-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
