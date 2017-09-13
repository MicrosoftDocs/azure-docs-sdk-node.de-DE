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
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="58840-104">Azure PostgreSQL-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="58840-104">Azure PostgreSQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="58840-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="58840-105">Overview</span></span>

<span data-ttu-id="58840-106">Für den Zugriff auf Azure-Datenbank für PostgreSQL wird die [Node.js-Verbindungsbibliothek für Azure-Datenbank für PostgreSQL](https://www.npmjs.com/package/pg) (Open Source) empfohlen.</span><span class="sxs-lookup"><span data-stu-id="58840-106">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="58840-107">Bei dieser Bibliothek handelt es sich um einen nicht blockierenden PostgreSQL-Client für Node.js, der reines JavaScript und optional native libpq-Bindungen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="58840-107">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="58840-108">Weitere Informationen zu [Azure-Datenbank für PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span><span class="sxs-lookup"><span data-stu-id="58840-108">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="58840-109">Clientpaket</span><span class="sxs-lookup"><span data-stu-id="58840-109">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="58840-110">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="58840-110">Install the npm module</span></span>

<span data-ttu-id="58840-111">Installieren Sie das PostgreSQL-Clientmodul mithilfe von npm.</span><span class="sxs-lookup"><span data-stu-id="58840-111">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="58840-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="58840-112">Example</span></span>

<span data-ttu-id="58840-113">Mit diesem Beispiel wird eine Clientverbindung geöffnet und eine einfache Abfrage ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="58840-113">This example opens a client connection and executes a simple query.</span></span>

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

## <a name="samples"></a><span data-ttu-id="58840-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="58840-114">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="58840-115">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="58840-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
