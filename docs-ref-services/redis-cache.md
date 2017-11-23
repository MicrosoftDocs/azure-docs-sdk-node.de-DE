---
title: "Azure Redis Cache-Module für Node.js"
description: "Referenz für Azure Redis Cache-Module für Node.js"
keywords: Azure, SDK, API, Redis Cache, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: 8a10e522e39461697b740750b63fc82a6cc320ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-redis-cache-modules-for-nodejs"></a><span data-ttu-id="067ba-104">Azure Redis Cache-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="067ba-104">Azure Redis Cache modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="067ba-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="067ba-105">Overview</span></span>

<span data-ttu-id="067ba-106">Azure Redis Cache basiert auf dem beliebten Open Source-Redis-Projekt.</span><span class="sxs-lookup"><span data-stu-id="067ba-106">Azure Redis Cache is based on the popular open source Redis project.</span></span> <span data-ttu-id="067ba-107">Sie erhalten Zugriff auf eine sichere, dedizierte Redis Cache-Instanz, die von Microsoft verwaltet wird und auf die aus Ihren Azure-Apps zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="067ba-107">It gives you access to a secure, dedicated Redis instance, managed by Microsoft and accessible from your Azure apps.</span></span>

<span data-ttu-id="067ba-108">Redis ist ein erweiterter Schlüsselwertspeicher, bei dem Schlüssel Datenstrukturen wie Zeichenfolgen, Hashes, Listen, Sätze und sortierte Sätze enthalten können.</span><span class="sxs-lookup"><span data-stu-id="067ba-108">Redis is an advanced key-value store, where keys can contain data structures such as strings, hashes, lists, sets, and sorted sets.</span></span> <span data-ttu-id="067ba-109">Redis unterstützt einen Satz automatischer Vorgänge für diese Datentypen.</span><span class="sxs-lookup"><span data-stu-id="067ba-109">Redis supports a set of atomic operations on these data types.</span></span>

<span data-ttu-id="067ba-110">Informieren Sie sich über [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).</span><span class="sxs-lookup"><span data-stu-id="067ba-110">Learn more about [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).</span></span>

## <a name="client-package"></a><span data-ttu-id="067ba-111">Clientpaket</span><span class="sxs-lookup"><span data-stu-id="067ba-111">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="067ba-112">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="067ba-112">Install the npm module</span></span>

<span data-ttu-id="067ba-113">Verwenden Sie npm, um das Redis-Modul für Node.js zu installieren.</span><span class="sxs-lookup"><span data-stu-id="067ba-113">Use npm to install the Redis module for Node.js</span></span>

```bash
npm install redis
```

### <a name="example"></a><span data-ttu-id="067ba-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="067ba-114">Example</span></span>

<span data-ttu-id="067ba-115">In diesem Beispiel wird eine Verbindung mit einer Azure Redis Cache-Instanz hergestellt und ein Schlüssel-Wert-Paar gespeichert. Anschließend wird der gespeicherte Wert anhand des Schlüssels gelesen.</span><span class="sxs-lookup"><span data-stu-id="067ba-115">This example connects to an Azure Redis Cache instance, stores a key/value pair and then reads the stored value by its key.</span></span>

```javascript
const redis = require('redis');

const client = redis.createClient(6380, '<name>.redis.cache.windows.net', {
  auth_pass: '<key>',
  tls: { servername: '<name>.redis.cache.windows.net' }
});

client.set('key1', 'value', (err, reply) => {
  console.log(reply);
});

client.get('key1', (err, reply) => {
  console.log(reply);
});
```

## <a name="management-package"></a><span data-ttu-id="067ba-116">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="067ba-116">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="067ba-117">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="067ba-117">Install the npm module</span></span>

<span data-ttu-id="067ba-118">Verwenden Sie npm, um die Azure Redis Cache-Module für Node.js zu installieren.</span><span class="sxs-lookup"><span data-stu-id="067ba-118">Use npm to install the Azure Redis Cache modules for Node.js</span></span>

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a><span data-ttu-id="067ba-119">Beispiel</span><span class="sxs-lookup"><span data-stu-id="067ba-119">Example</span></span>

<span data-ttu-id="067ba-120">In diesem Beispiel wird die Authentifizierung für Azure durchgeführt, und alle Redis Cache-Instanzen werden in einer angegebenen Ressourcengruppe aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="067ba-120">This example authenticates to Azure and lists all Redis Cache instances in a specified resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AzureMgmtRedisCache = require('azure-arm-rediscache');

msRestAzure.interactiveLogin().then(credentials => {
  const client = new AzureMgmtRedisCache(credentials, 'my-subscription-id');
  client.redis.listByResourceGroup('testResourceGroup').then(result => {
    console.log(result);
  });
});
```


## <a name="samples"></a><span data-ttu-id="067ba-121">Beispiele</span><span class="sxs-lookup"><span data-stu-id="067ba-121">Samples</span></span>

* [<span data-ttu-id="067ba-122">Verwenden von Azure Redis Cache mit Node.js</span><span class="sxs-lookup"><span data-stu-id="067ba-122">How to use Azure Redis Cache with Node.js</span></span>](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

<span data-ttu-id="067ba-123">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="067ba-123">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
