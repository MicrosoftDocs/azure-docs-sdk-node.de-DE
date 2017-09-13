---
title: "Azure SQL-Module für Node.js"
description: "Referenz zu Azure SQL-Modulen für Node.js"
keywords: Azure, Node, SDK, API, nodejs, javascript, sql
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 65ee90b4e6ca248b9d19a3685163211ca547cad4
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-sql-modules-for-nodejs"></a>Azure SQL-Module für Node.js

## <a name="overview"></a>Übersicht

Verwenden Sie in [Azure SQL-Datenbank](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) gespeicherte Daten über Node.js.
Über die Schnittstelle der Verwaltungsbibliothek können Sie Microsoft Azure SQL-Datenbanken ganz einfach verwalten.

## <a name="client-package"></a>Clientpaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls für den SQL Server-Client

```bash
npm install tedious
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel wird eine Verbindung mit einer SQL Server-Datenbank hergestellt und eine einfache Abfrage ausgeführt.

```javascript
const Connection = require('tedious').Connection;
const Request = require('tedious').Request;

const config = {
  userName: 'your-username',
  password: 'your-password',
  server: 'path-to-server',
  options: {
    database: 'database-name',
    encrypt: true
  }
};

const connection = new Connection(config);
connection.on('connect', err => {
  err ? console.log(err) : executeStatement();
});

const query = 'SELECT * from TableName';
const executeStatement = () => {
  const request = new Request(query, (err, rowCount) => {
    err ? console.log(err) : console.log(rowCount);
  });

  request.on('row', columns => {
    columns.forEach(column => console.log(column.value));
  });

  connection.execSql(request);
};
```

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-npm-modules"></a>Installieren der npm-Module

Installieren des npm-Moduls für die Azure SQL Server-Verwaltung

```
npm install azure-arm-sql
```   

### <a name="example"></a>Beispiel

Authentifizieren, Erstellen eines Clients und Auflisten aller Server:

```javascript
const msRestAzure = require('ms-rest-azure');
const SQLManagement = require('azure-arm-sql');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SQLManagement(credentials, 'your-subscription-id');
    return client.servers.list();
  })
  .then(servers => console.dir(servers, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Beispiele

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
