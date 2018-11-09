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
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "51098719"
---
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="a969a-103">Azure PostgreSQL-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="a969a-103">Azure PostgreSQL modules for Node.js</span></span>

<span data-ttu-id="a969a-104">Für den Zugriff auf Azure-Datenbank für PostgreSQL wird die [Node.js-Verbindungsbibliothek für Azure-Datenbank für PostgreSQL](https://www.npmjs.com/package/pg) (Open Source) empfohlen.</span><span class="sxs-lookup"><span data-stu-id="a969a-104">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="a969a-105">Bei dieser Bibliothek handelt es sich um einen nicht blockierenden PostgreSQL-Client für Node.js, der reines JavaScript und optional native libpq-Bindungen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a969a-105">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="a969a-106">Weitere Informationen zu [Azure-Datenbank für PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span><span class="sxs-lookup"><span data-stu-id="a969a-106">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="a969a-107">Clientpaket</span><span class="sxs-lookup"><span data-stu-id="a969a-107">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a969a-108">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="a969a-108">Install the npm module</span></span>

<span data-ttu-id="a969a-109">Installieren Sie das PostgreSQL-Clientmodul mithilfe von npm.</span><span class="sxs-lookup"><span data-stu-id="a969a-109">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="a969a-110">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a969a-110">Example</span></span>

<span data-ttu-id="a969a-111">Mit diesem Beispiel wird eine Clientverbindung geöffnet und eine einfache Abfrage ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="a969a-111">This example opens a client connection and executes a simple query.</span></span>

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

## <a name="samples"></a><span data-ttu-id="a969a-112">Beispiele</span><span class="sxs-lookup"><span data-stu-id="a969a-112">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="a969a-113">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="a969a-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
