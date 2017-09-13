---
title: "Azure Storage-Module für Node.js"
description: "Referenz zu Azure Storage-Modulen für Node.js"
keywords: Azure, Node, SDK, API, Storage, nodejs, javascript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: 61d3f3bb49d10e63a353c474067a155223bb6c76
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-storage-modules-for-nodejs"></a>Azure Storage-Module für Node.js

## <a name="overview"></a>Übersicht

Verwenden Sie das Azure Storage-Clientmodul für folgende Zwecke:

- Mit [Azure Blob Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage) können Sie Objekte und Dateien lesen und schreiben.
- Senden und Empfangen von Nachrichten zwischen Anwendungen mit Cloudverbindung per [Azure Queue Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)
- Lesen und Schreiben von großen strukturierten Datenmengen per [Azure Table Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)

Mit den Verwaltungsmodulen können Sie Azure Storage-Konten erstellen, aktualisieren und verwalten und Zugriffsschlüssel von Ihren Node.js-Apps abfragen und neu generieren.

## <a name="client-package"></a>Clientpaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren Sie das Azure Storage-npm-Clientmodul.

```bash
npm install azure-storage
```

### <a name="example"></a>Beispiel

In diesem Beispiel wird ein Speichercontainer erstellt und der Upload der lokalen Datei `data.txt` in den Container durchgeführt.

```javascript
const azure = require('azure-storage');
const blobService = azure.createBlobService(storageConnectionString);

const container = 'taskcontainer';
const task = 'taskblob';
const filename = 'data.txt';

blobService.createContainerIfNotExists(container, error => {
  if (error) return console.log(error);
  blobService.createBlockBlobFromLocalFile(
    container,
    task,
    filename,
    (error, result) => {
      if (error) return console.log(error);
      console.dir(result, { depth: null, colors: true });
    }
  );
});
```

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls 

Installieren Sie das Azure Storage-npm-Verwaltungsmodul.

```bash
npm install azure-arm-storage
```

### <a name="example"></a>Beispiel

In diesem Beispiel werden die Speicherkonten aufgelistet.

```javascript
const msRestAzure = require('ms-rest-azure');
const storageManagementClient = require('azure-arm-storage');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new storageManagementClient(
      credentials,
      subscriptionId
    );
    return client.storageAccounts.list();
  })
  .then(accounts => console.dir(accounts, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Beispiele

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
