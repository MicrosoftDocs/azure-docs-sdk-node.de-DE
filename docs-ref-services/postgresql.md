---
title: "Azure PostgreSQL-Module für Node.js"
description: "Referenz zu Azure PostgreSQL-Modulen für Node.js"
keywords: Azure, Node, SDK, API, nodejs, javascript, Datenbank, PostgreSQL
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: a5130c96b3ae922358b6898c15510282fbaa97f0
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-postgresql-modules-for-nodejs"></a>Azure PostgreSQL-Module für Node.js

## <a name="overview"></a>Übersicht

Für den Zugriff auf Azure-Datenbank für PostgreSQL wird die [Node.js-Verbindungsbibliothek für Azure-Datenbank für PostgreSQL](https://www.npmjs.com/package/pg) (Open Source) empfohlen. Bei dieser Bibliothek handelt es sich um einen nicht blockierenden PostgreSQL-Client für Node.js, der reines JavaScript und optional native libpq-Bindungen unterstützt.

Weitere Informationen zu [Azure-Datenbank für PostgreSQL](https://docs.microsoft.com/azure/postgresql/)

## <a name="client-package"></a>Clientpaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren Sie das PostgreSQL-Clientmodul mithilfe von npm.

```bash
npm install pg
```   

### <a name="example"></a>Beispiel

Mit diesem Beispiel wird eine Clientverbindung geöffnet und eine einfache Abfrage ausgeführt:

```javascript
const pg = require('pg');

const connectionString =
  'postgres://{username}@{server-name}:{password}@{server-name}.postgres.database.azure.com:5432/{database-name}?ssl=true';

const client = new pg.Client(connectionString);
client.connect();

const query = 'SELECT * FROM {table-name}';
client.query(query, (err, res) => {
  console.log(res);
});
```

## <a name="samples"></a>Beispiele

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
