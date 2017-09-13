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
# <a name="azure-redis-cache-modules-for-nodejs"></a>Azure Redis Cache-Module für Node.js

## <a name="overview"></a>Übersicht

Azure Redis Cache basiert auf dem beliebten Open Source-Redis-Projekt. Sie erhalten Zugriff auf eine sichere, dedizierte Redis Cache-Instanz, die von Microsoft verwaltet wird und auf die aus Ihren Azure-Apps zugegriffen werden kann.

Redis ist ein erweiterter Schlüsselwertspeicher, bei dem Schlüssel Datenstrukturen wie Zeichenfolgen, Hashes, Listen, Sätze und sortierte Sätze enthalten können. Redis unterstützt einen Satz automatischer Vorgänge für diese Datentypen.

Informieren Sie sich über [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).

## <a name="client-package"></a>Clientpaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Verwenden Sie npm, um das Redis-Modul für Node.js zu installieren.

```bash
npm install redis
```

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine Verbindung mit einer Azure Redis Cache-Instanz hergestellt und ein Schlüssel-Wert-Paar gespeichert. Anschließend wird der gespeicherte Wert anhand des Schlüssels gelesen.

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

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Verwenden Sie npm, um die Azure Redis Cache-Module für Node.js zu installieren.

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a>Beispiel

In diesem Beispiel wird die Authentifizierung für Azure durchgeführt, und alle Redis Cache-Instanzen werden in einer angegebenen Ressourcengruppe aufgeführt.

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


## <a name="samples"></a>Beispiele

* [Verwenden von Azure Redis Cache mit Node.js](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
