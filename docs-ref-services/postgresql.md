---
title: "Azure PostgreSQL-Module für Node.js"
description: "Referenz zu Azure PostgreSQL-Modulen für Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: d8a2c7fe90746def7e50a7af3a0f470213eed197
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2018
---
# <a name="azure-postgresql-modules-for-nodejs"></a>Azure PostgreSQL-Module für Node.js

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

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
