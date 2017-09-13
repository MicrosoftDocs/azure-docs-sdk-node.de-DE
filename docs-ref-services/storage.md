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
# <a name="azure-storage-modules-for-nodejs"></a><span data-ttu-id="9fa57-104">Azure Storage-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="9fa57-104">Azure Storage modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="9fa57-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="9fa57-105">Overview</span></span>

<span data-ttu-id="9fa57-106">Verwenden Sie das Azure Storage-Clientmodul für folgende Zwecke:</span><span class="sxs-lookup"><span data-stu-id="9fa57-106">Use the Azure Storage client module to:</span></span>

- <span data-ttu-id="9fa57-107">Mit [Azure Blob Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage) können Sie Objekte und Dateien lesen und schreiben.</span><span class="sxs-lookup"><span data-stu-id="9fa57-107">Read and write objects and files from [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span></span>
- <span data-ttu-id="9fa57-108">Senden und Empfangen von Nachrichten zwischen Anwendungen mit Cloudverbindung per [Azure Queue Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span><span class="sxs-lookup"><span data-stu-id="9fa57-108">Send and receive messages between cloud-connected applications with [Azure Queue storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span></span>
- <span data-ttu-id="9fa57-109">Lesen und Schreiben von großen strukturierten Datenmengen per [Azure Table Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span><span class="sxs-lookup"><span data-stu-id="9fa57-109">Read and write large structured data with [Azure Table storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span></span>

<span data-ttu-id="9fa57-110">Mit den Verwaltungsmodulen können Sie Azure Storage-Konten erstellen, aktualisieren und verwalten und Zugriffsschlüssel von Ihren Node.js-Apps abfragen und neu generieren.</span><span class="sxs-lookup"><span data-stu-id="9fa57-110">Create, update, and manage Azure Storage accounts and query and regenerate access keys from your Node.js apps with the management modules.</span></span>

## <a name="client-package"></a><span data-ttu-id="9fa57-111">Clientpaket</span><span class="sxs-lookup"><span data-stu-id="9fa57-111">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9fa57-112">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="9fa57-112">Install the npm module</span></span>

<span data-ttu-id="9fa57-113">Installieren Sie das Azure Storage-npm-Clientmodul.</span><span class="sxs-lookup"><span data-stu-id="9fa57-113">Install the Azure storage client npm module</span></span>

```bash
npm install azure-storage
```

### <a name="example"></a><span data-ttu-id="9fa57-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="9fa57-114">Example</span></span>

<span data-ttu-id="9fa57-115">In diesem Beispiel wird ein Speichercontainer erstellt und der Upload der lokalen Datei `data.txt` in den Container durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="9fa57-115">This example create a storage container and uploads a local file `data.txt` to it.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="9fa57-116">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="9fa57-116">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9fa57-117">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="9fa57-117">Install the npm module</span></span> 

<span data-ttu-id="9fa57-118">Installieren Sie das Azure Storage-npm-Verwaltungsmodul.</span><span class="sxs-lookup"><span data-stu-id="9fa57-118">Install the Azure storage management npm module</span></span>

```bash
npm install azure-arm-storage
```

### <a name="example"></a><span data-ttu-id="9fa57-119">Beispiel</span><span class="sxs-lookup"><span data-stu-id="9fa57-119">Example</span></span>

<span data-ttu-id="9fa57-120">In diesem Beispiel werden die Speicherkonten aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="9fa57-120">This example list the storage accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="9fa57-121">Beispiele</span><span class="sxs-lookup"><span data-stu-id="9fa57-121">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

<span data-ttu-id="9fa57-122">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="9fa57-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
