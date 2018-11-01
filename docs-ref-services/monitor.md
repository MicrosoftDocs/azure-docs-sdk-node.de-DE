---
title: Azure Monitor-Module für Node.js
description: Referenz zu Azure Monitor-Modulen für Node.js
author: rbouche
ms.author: robb
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: fb2cc5ba927fe03fb5fe3114919ed1b0b6e969ae
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50346348"
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="d0848-103">Azure Monitor-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="d0848-103">Azure Monitor modules for Node.js</span></span>

<span data-ttu-id="d0848-104">Cloudanwendungen sind komplexe Systeme mit zahlreichen Variablen.</span><span class="sxs-lookup"><span data-stu-id="d0848-104">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="d0848-105">Die Überwachung stellt Daten bereit, auf deren Grundlage die ordnungsgemäße Ausführung der Anwendung sichergestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="d0848-105">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="d0848-106">Sie trägt auch zur Vermeidung potenzieller Probleme bei und hilft bei der Behandlung bereits aufgetretener Probleme.</span><span class="sxs-lookup"><span data-stu-id="d0848-106">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="d0848-107">Darüber hinaus können Sie auf der Grundlage von Überwachungsdaten umfassende Erkenntnisse über Ihre Anwendung gewinnen.</span><span class="sxs-lookup"><span data-stu-id="d0848-107">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="d0848-108">Mithilfe dieser Kenntnisse können Sie die Leistung oder Wartungsfreundlichkeit der Anwendung verbessern oder Aktionen automatisieren, die andernfalls manuell ausgeführt werden müssten.</span><span class="sxs-lookup"><span data-stu-id="d0848-108">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="d0848-109">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="d0848-109">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="d0848-110">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="d0848-110">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="d0848-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d0848-111">Example</span></span>

<span data-ttu-id="d0848-112">Mit diesem Codebeispiel werden alle einer Ressourcengruppe zugeordnete Warnungsregeln ausgegeben:</span><span class="sxs-lookup"><span data-stu-id="d0848-112">This code example prints all the alerting rules associated with a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const monitorManagementClient = require('azure-arm-monitor');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new monitorManagementClient(credentials, subscriptionId);
    client.alertRules.listByResourceGroup(resourceGroupName, rules => {
      console.log('List of rules:');
      console.dir(rules, { depth: null, colors: true });
    })
  });
```

### <a name="samples"></a><span data-ttu-id="d0848-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="d0848-113">Samples</span></span>

<span data-ttu-id="d0848-114">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d0848-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
