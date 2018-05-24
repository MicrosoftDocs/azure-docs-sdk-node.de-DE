---
title: Azure Automation-Module für Node.js
description: Referenz zu Azure Automation-Modulen für Node.js
author: eamonoreilly
ms.author: eamono
manager: nirb
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 5efe0c0633313bcf489b05b8a54f71bba9a00da5
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="8d4dd-103">Azure Automation-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="8d4dd-103">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="8d4dd-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="8d4dd-104">Overview</span></span>

<span data-ttu-id="8d4dd-105">Azure Automation ermöglicht es Benutzern, die manuellen, längeren, fehleranfälligen und häufig wiederholten Aufgaben zu automatisieren, die in einer Cloud- und Unternehmensumgebung normalerweise ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8d4dd-105">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="8d4dd-106">Automation spart Zeit, erhöht die Zuverlässigkeit normaler Verwaltungsaufgaben und plant diese sogar so ein, dass sie in regelmäßigen Abständen automatisch ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8d4dd-106">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="8d4dd-107">Sie können Prozesse mit Runbooks automatisieren oder die Konfigurationsverwaltung über die Konfiguration für den gewünschten Zustand automatisieren.</span><span class="sxs-lookup"><span data-stu-id="8d4dd-107">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="8d4dd-108">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="8d4dd-108">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="8d4dd-109">Installieren der Module mit npm</span><span class="sxs-lookup"><span data-stu-id="8d4dd-109">Install the modules with npm</span></span>

<span data-ttu-id="8d4dd-110">Installieren der Azure Automation-Module für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="8d4dd-110">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="8d4dd-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8d4dd-111">Example</span></span>

<span data-ttu-id="8d4dd-112">Mit diesem Beispiel werden die Automation-Konten aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="8d4dd-112">This example lists the automation accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));

```

## <a name="samples"></a><span data-ttu-id="8d4dd-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="8d4dd-113">Samples</span></span>

<span data-ttu-id="8d4dd-114">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="8d4dd-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
