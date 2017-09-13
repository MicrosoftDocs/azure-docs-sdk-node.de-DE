---
title: "Azure Monitor-Module für Node.js"
description: "Referenz zu Azure Monitor-Modulen für Node.js"
keywords: Azure,SDK,API,Monitor, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 8d27d837bddaa5258dde47b769cf601f6f5a861f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="c703b-104">Azure Monitor-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="c703b-104">Azure Monitor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c703b-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="c703b-105">Overview</span></span>
<span data-ttu-id="c703b-106">Cloudanwendungen sind komplexe Systeme mit zahlreichen Variablen.</span><span class="sxs-lookup"><span data-stu-id="c703b-106">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="c703b-107">Die Überwachung stellt Daten bereit, auf deren Grundlage die ordnungsgemäße Ausführung der Anwendung sichergestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="c703b-107">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="c703b-108">Sie trägt auch zur Vermeidung potenzieller Probleme bei und hilft bei der Behandlung bereits aufgetretener Probleme.</span><span class="sxs-lookup"><span data-stu-id="c703b-108">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="c703b-109">Darüber hinaus können Sie auf der Grundlage von Überwachungsdaten umfassende Erkenntnisse über Ihre Anwendung gewinnen.</span><span class="sxs-lookup"><span data-stu-id="c703b-109">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="c703b-110">Mithilfe dieser Kenntnisse können Sie die Leistung oder Wartungsfreundlichkeit der Anwendung verbessern oder Aktionen automatisieren, die andernfalls manuell ausgeführt werden müssten.</span><span class="sxs-lookup"><span data-stu-id="c703b-110">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="c703b-111">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="c703b-111">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="c703b-112">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="c703b-112">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="c703b-113">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c703b-113">Example</span></span>

<span data-ttu-id="c703b-114">Mit diesem Codebeispiel werden alle einer Ressourcengruppe zugeordnete Warnungsregeln ausgegeben:</span><span class="sxs-lookup"><span data-stu-id="c703b-114">This code example prints all the alerting rules associated with a resource group.</span></span>

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

### <a name="samples"></a><span data-ttu-id="c703b-115">Beispiele</span><span class="sxs-lookup"><span data-stu-id="c703b-115">Samples</span></span>

<span data-ttu-id="c703b-116">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c703b-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
