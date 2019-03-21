---
title: Azure Backup-Module für Node.js
description: Referenz zu Azure Backup-Modulen für Node.js
author: markgalioto
ms.author: markgal
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: 9234285d32bc465eeb86d13514783e1de4e5ef1b
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052788"
---
# <a name="azure-backup-modules-for-nodejs"></a><span data-ttu-id="7338b-103">Azure Backup-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="7338b-103">Azure Backup Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="7338b-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="7338b-104">Overview</span></span>

<span data-ttu-id="7338b-105">Azure Backup ist der Azure-basierte Dienst, den Sie zum Sichern (bzw. Schützen) und Wiederherstellen Ihrer Daten in der Microsoft Cloud verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7338b-105">Azure Backup is the Azure-based service you can use to back up (or protect) and restore your data in the Microsoft cloud.</span></span> <span data-ttu-id="7338b-106">Azure Backup ersetzt Ihre vorhandene lokale bzw. standortexterne Lösung durch eine zuverlässige, sichere und wirtschaftliche Cloudlösung.</span><span class="sxs-lookup"><span data-stu-id="7338b-106">Azure Backup replaces your existing on-premises or off-site backup solution with a cloud-based solution that is reliable, secure, and cost-competitive.</span></span> <span data-ttu-id="7338b-107">Azure Backup verfügt über mehrere Komponenten, die Sie herunterladen und auf dem jeweiligen Computer, Server oder in der Cloud bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="7338b-107">Azure Backup offers multiple components that you download and deploy on the appropriate computer, server, or in the cloud.</span></span> <span data-ttu-id="7338b-108">Die Komponente (der Agent), die Sie bereitstellen, richtet sich danach, was geschützt werden soll.</span><span class="sxs-lookup"><span data-stu-id="7338b-108">The component, or agent, that you deploy depends on what you want to protect.</span></span> <span data-ttu-id="7338b-109">Alle Azure Backup-Komponenten (unabhängig davon, ob Daten lokal oder in der Cloud geschützt werden sollen) können genutzt werden, um Daten in einem Recovery Services-Tresor in Azure zu sichern.</span><span class="sxs-lookup"><span data-stu-id="7338b-109">All Azure Backup components (no matter whether you're protecting data on-premises or in the cloud) can be used to back up data to a Recovery Services vault in Azure.</span></span> 

## <a name="management-package"></a><span data-ttu-id="7338b-110">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="7338b-110">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="7338b-111">Installieren der Module mit npm</span><span class="sxs-lookup"><span data-stu-id="7338b-111">Install the modules with npm</span></span>

<span data-ttu-id="7338b-112">Installieren der Azure Backup-Module für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="7338b-112">Use npm to install the Azure Backup modules for Node.js</span></span>

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a><span data-ttu-id="7338b-113">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7338b-113">Example</span></span>

<span data-ttu-id="7338b-114">Mit diesem Beispiel werden die Wiederherstellungsaufträge für einen bestimmten Tresor und eine bestimmte Ressourcengruppe aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="7338b-114">This example lists the recovery jobs for a given vault and resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="7338b-115">Beispiele</span><span class="sxs-lookup"><span data-stu-id="7338b-115">Samples</span></span>

<span data-ttu-id="7338b-116">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7338b-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
