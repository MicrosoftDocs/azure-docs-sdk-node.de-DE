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
# <a name="azure-cosmos-db-modules-for-nodejs"></a>Azure Cosmos DB-Module für Node.js

## <a name="overview"></a>Übersicht

Azure Cosmos DB ist eine global verteilte Datenbank von Microsoft mit mehreren Modellen. Azure Cosmos DB ermöglicht es Ihnen, Durchsatz und Speicher elastisch und unabhängig voneinander über eine beliebige Anzahl von geografischen Azure-Regionen hinweg zu skalieren. Azure Cosmos DB bietet Ihnen mit umfassenden Vereinbarungen zum Servicelevel (Service Level Agreements, SLAs) Durchsatz-, Wartezeit-, Verfügbarkeits- und Konsistenzgarantien wie kein anderer Datenbankdienst.

Azure Cosmos DB enthält ein ressourcengesteuertes, vom Schema unabhängiges Datenbankmodul mit optimierten Schreibvorgängen, die mehrere Datenmodelle nativ unterstützt: Schlüssel-Wert-, Dokumenten-, Graph- und spaltenbasierte Datenmodelle. Azure Cosmos DB unterstützt zudem viele APIs für den Zugriff auf Daten, z.B. MongoDB, DocumentDB SQL, Gremlin (Vorschauversion) und Azure-Tabellen (Vorschauversion), und ist erweiterbar.

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls 

Installieren des npm-Moduls für Azure Cosmos DB

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel werden alle Cosmos DB-Konten aufgeführt:

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

## <a name="samples"></a>Beispiele

* [Entwickeln einer Node.js-App mit Azure Cosmos DB – DocumentDB](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [Entwickeln einer Node.js-App mit Azure Cosmos DB – Gremlin](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
