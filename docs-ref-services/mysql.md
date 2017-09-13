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
# <a name="azure-mysql-modules-for-nodejs"></a>Azure MySQL-Module für Node.js

## <a name="overview"></a>Übersicht

Für den Zugriff auf Azure-Datenbank für MySQL wird die [Node.js-Verbindungsbibliothek für Azure-Datenbank für MySQL](https://github.com/sidorares/node-mysql2) (Open Source) empfohlen. 

Weitere Informationen zu [Azure-Datenbank für MySQL](https://docs.microsoft.com/azure/MySQL/)

## <a name="client-package"></a>Clientpaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren Sie das MySQL-Clientmodul mithilfe von npm.

```bash
npm install mysql2
```   

### <a name="example"></a>Beispiel

Mit diesem Beispiel wird eine Verbindung mit einer MySQL-Datenbank hergestellt und eine einfache Abfrage ausgeführt, um alle Kunden abzurufen.

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

## <a name="samples"></a>Beispiele

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
