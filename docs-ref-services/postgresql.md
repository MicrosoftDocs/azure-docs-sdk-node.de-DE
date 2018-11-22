---
title: Azure PostgreSQL-Module für Node.js
description: Referenz zu Azure PostgreSQL-Modulen für Node.js
author: rachel-msft
ms.author: raagyema
manager: sukamat
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: ed9373b767684e4893ca84de1030d062178b7ea4
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2018
ms.locfileid: "52003754"
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
