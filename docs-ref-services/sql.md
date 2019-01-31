---
title: Azure SQL-Module für Node.js
description: Referenz zu Azure SQL-Modulen für Node.js
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: sql-database
ms.subservice: development
ms.openlocfilehash: 00ba5984b5f8aef85570c54f23efefd1d741ca57
ms.sourcegitcommit: 0e294f7c4dcdfae9df18ff3e82b6563680ef2519
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55046430"
---
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="382d6-103">Azure SQL-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="382d6-103">Azure SQL modules for Node.js</span></span>

<span data-ttu-id="382d6-104">Verwenden Sie in [Azure SQL-Datenbank](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) gespeicherte Daten über Node.js.</span><span class="sxs-lookup"><span data-stu-id="382d6-104">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="382d6-105">Über die Schnittstelle der Verwaltungsbibliothek können Sie Microsoft Azure SQL-Datenbanken ganz einfach verwalten.</span><span class="sxs-lookup"><span data-stu-id="382d6-105">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="382d6-106">Clientpaket</span><span class="sxs-lookup"><span data-stu-id="382d6-106">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="382d6-107">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="382d6-107">Install the npm module</span></span>

<span data-ttu-id="382d6-108">Installieren des npm-Moduls für den SQL Server-Client</span><span class="sxs-lookup"><span data-stu-id="382d6-108">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="382d6-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="382d6-109">Example</span></span>

<span data-ttu-id="382d6-110">Mit diesem Beispiel wird eine Verbindung mit einer SQL Server-Datenbank hergestellt und eine einfache Abfrage ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="382d6-110">This example connects to a SQL Server database and perform a simple query.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="382d6-111">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="382d6-111">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="382d6-112">Installieren der npm-Module</span><span class="sxs-lookup"><span data-stu-id="382d6-112">Install npm modules</span></span>

<span data-ttu-id="382d6-113">Installieren des npm-Moduls für die Azure SQL Server-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="382d6-113">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="382d6-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="382d6-114">Example</span></span>

<span data-ttu-id="382d6-115">Authentifizieren, Erstellen eines Clients und Auflisten aller Server:</span><span class="sxs-lookup"><span data-stu-id="382d6-115">Authenticate, create a client, and list all servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="382d6-116">Beispiele</span><span class="sxs-lookup"><span data-stu-id="382d6-116">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="382d6-117">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="382d6-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
