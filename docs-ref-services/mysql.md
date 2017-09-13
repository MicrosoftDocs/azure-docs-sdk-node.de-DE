---
title: "Azure MySQL-Module für Node.js"
description: "Referenz zu Azure MySQL-Modulen für Node.js"
keywords: Azure, Node, SDK, API, nodejs, javascript, Datenbank, MySQL
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 3efc0fcccb7cb01711ad1ce98e9ff9a2d87b77fe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="1569d-104">Azure MySQL-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="1569d-104">Azure MySQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="1569d-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="1569d-105">Overview</span></span>

<span data-ttu-id="1569d-106">Für den Zugriff auf Azure-Datenbank für MySQL wird die [Node.js-Verbindungsbibliothek für Azure-Datenbank für MySQL](https://github.com/sidorares/node-mysql2) (Open Source) empfohlen.</span><span class="sxs-lookup"><span data-stu-id="1569d-106">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="1569d-107">Weitere Informationen zu [Azure-Datenbank für MySQL](https://docs.microsoft.com/azure/MySQL/)</span><span class="sxs-lookup"><span data-stu-id="1569d-107">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="1569d-108">Clientpaket</span><span class="sxs-lookup"><span data-stu-id="1569d-108">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1569d-109">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="1569d-109">Install the npm module</span></span>

<span data-ttu-id="1569d-110">Installieren Sie das MySQL-Clientmodul mithilfe von npm.</span><span class="sxs-lookup"><span data-stu-id="1569d-110">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="1569d-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="1569d-111">Example</span></span>

<span data-ttu-id="1569d-112">Mit diesem Beispiel wird eine Verbindung mit einer MySQL-Datenbank hergestellt und eine einfache Abfrage ausgeführt, um alle Kunden abzurufen.</span><span class="sxs-lookup"><span data-stu-id="1569d-112">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

```javascript
const mysql = require('mysql2');

const connection = mysql.createConnection({
  host: 'mysqldemo.mysql.database.azure.com',
  user: 'myadmin@mysqldemo',
  password: 'your_password',
  database: 'my_db',
  port: 3306,
  ssl: true
});

connection.connect();
const query = 'SELECT * FROM customers';
connection.query(query, (err, res) =>
  console.log(`We have ${res.length} customers`)
);

connection.end();
```

## <a name="samples"></a><span data-ttu-id="1569d-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="1569d-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="1569d-114">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="1569d-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
