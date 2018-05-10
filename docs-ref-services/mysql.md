---
title: Azure MySQL-Module für Node.js
description: Referenz zu Azure MySQL-Modulen für Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 21b98aeba1e21ec1d9f7da4a115110fffe05b2b8
ms.sourcegitcommit: b4cf45cb23da56718b482cf7fc240c592e15206b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="ef461-103">Azure MySQL-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="ef461-103">Azure MySQL modules for Node.js</span></span>

<span data-ttu-id="ef461-104">Für den Zugriff auf Azure-Datenbank für MySQL wird die [Node.js-Verbindungsbibliothek für Azure-Datenbank für MySQL](https://github.com/sidorares/node-mysql2) (Open Source) empfohlen.</span><span class="sxs-lookup"><span data-stu-id="ef461-104">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="ef461-105">Weitere Informationen zu [Azure-Datenbank für MySQL](https://docs.microsoft.com/azure/MySQL/)</span><span class="sxs-lookup"><span data-stu-id="ef461-105">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="ef461-106">Clientpaket</span><span class="sxs-lookup"><span data-stu-id="ef461-106">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ef461-107">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="ef461-107">Install the npm module</span></span>

<span data-ttu-id="ef461-108">Installieren Sie das MySQL-Clientmodul mithilfe von npm.</span><span class="sxs-lookup"><span data-stu-id="ef461-108">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="ef461-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ef461-109">Example</span></span>

<span data-ttu-id="ef461-110">Mit diesem Beispiel wird eine Verbindung mit einer MySQL-Datenbank hergestellt und eine einfache Abfrage ausgeführt, um alle Kunden abzurufen.</span><span class="sxs-lookup"><span data-stu-id="ef461-110">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ef461-111">Beispiele</span><span class="sxs-lookup"><span data-stu-id="ef461-111">Samples</span></span>

[!INCLUDE [node-mysql-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="ef461-112">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="ef461-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
