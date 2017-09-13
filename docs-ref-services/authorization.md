---
title: "Azure-Autorisierungsmodule für Node.js"
description: "Referenz zu Azure-Autorisierungsmodulen für Node.js"
keywords: Azure,SDK,API,Autorisierung, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: de843bf1afed77afdb9bde035962a1c151d9c1bb
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="b4593-104">Azure-Autorisierungsmodule für Node.js</span><span class="sxs-lookup"><span data-stu-id="b4593-104">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b4593-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="b4593-105">Overview</span></span>

<span data-ttu-id="b4593-106">Mithilfe des Authentifizierungs-/Autorisierungsfeatures von Azure App Service kann Ihre Anwendung Benutzer anmelden, sodass Sie keine Codeänderungen für das Back-End der App vornehmen müssen.</span><span class="sxs-lookup"><span data-stu-id="b4593-106">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="b4593-107">Die Autorisierung stellt eine einfache Möglichkeit zum Schutz Ihrer Anwendung und für die Arbeit mit benutzerspezifischen Daten bereit.</span><span class="sxs-lookup"><span data-stu-id="b4593-107">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="b4593-108">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="b4593-108">Management package</span></span>

<span data-ttu-id="b4593-109">Installieren der Azure-Autorisierungsmodule für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="b4593-109">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b4593-110">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="b4593-110">Install the npm module</span></span>

<span data-ttu-id="b4593-111">Installieren des npm-Moduls für Azure-Autorisierung</span><span class="sxs-lookup"><span data-stu-id="b4593-111">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="b4593-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b4593-112">Example</span></span>

<span data-ttu-id="b4593-113">Mit diesem Beispiel werden alle Rollenzuweisungen für die angeforderte Ressourcengruppe aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="b4593-113">This example lists all role assignments for the requested resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const authorizationManagement = require('azure-arm-authorization');

const resourceGroup = 'resource-group-name';
const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
 const client = new authorizationManagement(credentials, subscriptionId);
 client.roleAssignments.listForResourceGroup(resourceGroupName).then(result => {
   console.log(result);
 });
});
```

## <a name="samples"></a><span data-ttu-id="b4593-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="b4593-114">Samples</span></span>

<span data-ttu-id="b4593-115">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="b4593-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
