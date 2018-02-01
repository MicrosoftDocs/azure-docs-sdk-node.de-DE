---
title: "Azure Storage-Module für Node.js"
description: "Referenz zu Azure Storage-Modulen für Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: b94c6fbb50e656e0dcc542236afe791c7ddc9be4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2018
---
# <a name="azure-storage-modules-for-nodejs"></a><span data-ttu-id="55c1f-103">Azure Storage-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="55c1f-103">Azure Storage modules for Node.js</span></span>

<span data-ttu-id="55c1f-104">Verwenden Sie das Azure Storage-Clientmodul für folgende Zwecke:</span><span class="sxs-lookup"><span data-stu-id="55c1f-104">Use the Azure Storage client module to:</span></span>

- <span data-ttu-id="55c1f-105">Mit [Azure Blob Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage) können Sie Objekte und Dateien lesen und schreiben.</span><span class="sxs-lookup"><span data-stu-id="55c1f-105">Read and write objects and files from [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span></span>
- <span data-ttu-id="55c1f-106">Senden und Empfangen von Nachrichten zwischen Anwendungen mit Cloudverbindung per [Azure Queue Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span><span class="sxs-lookup"><span data-stu-id="55c1f-106">Send and receive messages between cloud-connected applications with [Azure Queue storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span></span>
- <span data-ttu-id="55c1f-107">Lesen und Schreiben von großen strukturierten Datenmengen per [Azure Table Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span><span class="sxs-lookup"><span data-stu-id="55c1f-107">Read and write large structured data with [Azure Table storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span></span>

<span data-ttu-id="55c1f-108">Mit den Verwaltungsmodulen können Sie Azure Storage-Konten erstellen, aktualisieren und verwalten und Zugriffsschlüssel von Ihren Node.js-Apps abfragen und neu generieren.</span><span class="sxs-lookup"><span data-stu-id="55c1f-108">Create, update, and manage Azure Storage accounts and query and regenerate access keys from your Node.js apps with the management modules.</span></span>

## <a name="client-package"></a><span data-ttu-id="55c1f-109">Clientpaket</span><span class="sxs-lookup"><span data-stu-id="55c1f-109">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="55c1f-110">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="55c1f-110">Install the npm module</span></span>

<span data-ttu-id="55c1f-111">Installieren Sie das Azure Storage-npm-Clientmodul.</span><span class="sxs-lookup"><span data-stu-id="55c1f-111">Install the Azure storage client npm module</span></span>

```bash
npm install azure-storage
```

### <a name="example"></a><span data-ttu-id="55c1f-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="55c1f-112">Example</span></span>

<span data-ttu-id="55c1f-113">In diesem Beispiel wird ein Speichercontainer erstellt und der Upload der lokalen Datei `data.txt` in den Container durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="55c1f-113">This example create a storage container and uploads a local file `data.txt` to it.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="55c1f-114">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="55c1f-114">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="55c1f-115">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="55c1f-115">Install the npm module</span></span> 

<span data-ttu-id="55c1f-116">Installieren Sie das Azure Storage-npm-Verwaltungsmodul.</span><span class="sxs-lookup"><span data-stu-id="55c1f-116">Install the Azure storage management npm module</span></span>

```bash
npm install azure-arm-storage
```

### <a name="example"></a><span data-ttu-id="55c1f-117">Beispiel</span><span class="sxs-lookup"><span data-stu-id="55c1f-117">Example</span></span>

<span data-ttu-id="55c1f-118">In diesem Beispiel werden die Speicherkonten aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="55c1f-118">This example list the storage accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="55c1f-119">Beispiele</span><span class="sxs-lookup"><span data-stu-id="55c1f-119">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

<span data-ttu-id="55c1f-120">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="55c1f-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
