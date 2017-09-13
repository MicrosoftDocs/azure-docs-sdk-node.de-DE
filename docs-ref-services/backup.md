---
title: "Azure Backup-Module für Node.js"
description: "Referenz zu Azure Backup-Modulen für Node.js"
keywords: Azure,SDK,API,Backup, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: 3ff9bff16a520bca461198531fd4c02139d2b293
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-backup-modules-for-nodejs"></a><span data-ttu-id="67413-104">Azure Backup-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="67413-104">Azure Backup Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="67413-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="67413-105">Overview</span></span>

<span data-ttu-id="67413-106">Azure Backup ist der Azure-basierte Dienst, den Sie zum Sichern (bzw. Schützen) und Wiederherstellen Ihrer Daten in der Microsoft Cloud verwenden können.</span><span class="sxs-lookup"><span data-stu-id="67413-106">Azure Backup is the Azure-based service you can use to back up (or protect) and restore your data in the Microsoft cloud.</span></span> <span data-ttu-id="67413-107">Azure Backup ersetzt Ihre vorhandene lokale bzw. standortexterne Lösung durch eine zuverlässige, sichere und wirtschaftliche Cloudlösung.</span><span class="sxs-lookup"><span data-stu-id="67413-107">Azure Backup replaces your existing on-premises or off-site backup solution with a cloud-based solution that is reliable, secure, and cost-competitive.</span></span> <span data-ttu-id="67413-108">Azure Backup verfügt über mehrere Komponenten, die Sie herunterladen und auf dem jeweiligen Computer, Server oder in der Cloud bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="67413-108">Azure Backup offers multiple components that you download and deploy on the appropriate computer, server, or in the cloud.</span></span> <span data-ttu-id="67413-109">Die Komponente (der Agent), die Sie bereitstellen, richtet sich danach, was geschützt werden soll.</span><span class="sxs-lookup"><span data-stu-id="67413-109">The component, or agent, that you deploy depends on what you want to protect.</span></span> <span data-ttu-id="67413-110">Alle Azure Backup-Komponenten (unabhängig davon, ob Daten lokal oder in der Cloud geschützt werden sollen) können genutzt werden, um Daten in einem Recovery Services-Tresor in Azure zu sichern.</span><span class="sxs-lookup"><span data-stu-id="67413-110">All Azure Backup components (no matter whether you're protecting data on-premises or in the cloud) can be used to back up data to a Recovery Services vault in Azure.</span></span> 

## <a name="management-package"></a><span data-ttu-id="67413-111">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="67413-111">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="67413-112">Installieren der Module mit npm</span><span class="sxs-lookup"><span data-stu-id="67413-112">Install the modules with npm</span></span>

<span data-ttu-id="67413-113">Installieren der Azure Backup-Module für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="67413-113">Use npm to install the Azure Backup modules for Node.js</span></span>

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a><span data-ttu-id="67413-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="67413-114">Example</span></span>

<span data-ttu-id="67413-115">Mit diesem Beispiel werden die Wiederherstellungsaufträge für einen bestimmten Tresor und eine bestimmte Ressourcengruppe aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="67413-115">This example lists the recovery jobs for a given vault and resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesBackupManagement = require('azure-arm-recoveryservicesbackup');

const subcriptionId = 'your-subscription-id';
const vault = 'your-recovery-service-vault';
const resourceGroupName = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesBackupManagement(
      credentials,
      subcriptionId
    );
    return client.jobs.list(vault, resourceGroupName);
  })
  .then(jobs => console.dir(jobs, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="67413-116">Beispiele</span><span class="sxs-lookup"><span data-stu-id="67413-116">Samples</span></span>

<span data-ttu-id="67413-117">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="67413-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
