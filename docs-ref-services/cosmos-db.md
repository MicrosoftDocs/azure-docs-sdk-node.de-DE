---
title: Azure Cosmos DB-Module für Node.js
description: Referenz zu Azure Cosmos DB-Modulen für Node.js
author: SnehaGunda
ms.author: sngun
manager: kfile
ms.date: 03/20/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 4064f9f6c0e1369c8d6261a70709102e7492b340
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260756"
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a>Azure Cosmos DB-Module für Node.js

Azure Cosmos DB ist eine global verteilte Datenbank von Microsoft mit mehreren Modellen. Azure Cosmos DB ermöglicht es Ihnen, Durchsatz und Speicher elastisch und unabhängig voneinander über eine beliebige Anzahl von geografischen Azure-Regionen hinweg zu skalieren. Azure Cosmos DB bietet Ihnen mit umfassenden Vereinbarungen zum Servicelevel (Service Level Agreements, SLAs) Durchsatz-, Wartezeit-, Verfügbarkeits- und Konsistenzgarantien wie kein anderer Datenbankdienst.

Azure Cosmos DB umfasst eine ressourcengesteuerte, vom Schema unabhängige Datenbank-Engine mit optimierten Schreibvorgängen, die mehrere Datenmodelle nativ unterstützt: Schlüssel-Wert-, Dokumenten-, Graph- und spaltenbasierte Datenmodelle. Azure Cosmos DB unterstützt zudem viele APIs für den Zugriff auf Daten, z.B. MongoDB, SQL, Gremlin/Graph, Azure Tables und Cassandra (Vorschauversion) und ist erweiterbar.

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls 

Installieren Sie das npm-Modul für Azure Cosmos DB.

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel werden alle Azure Cosmos DB-Konten aufgeführt.

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

* [Entwickeln einer Node.js-App mit Azure Cosmos DB](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [Entwickeln einer Node.js-App mit Azure Cosmos DB – Gremlin](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
