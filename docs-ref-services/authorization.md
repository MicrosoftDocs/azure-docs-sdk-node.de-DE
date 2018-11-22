---
title: Azure-Autorisierungsmodule für Node.js
description: Referenz zu Azure-Autorisierungsmodulen für Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 0b0ecd088d8b7728e56f352597e2db038678945f
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2018
ms.locfileid: "52048375"
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="e52a4-103">Azure-Autorisierungsmodule für Node.js</span><span class="sxs-lookup"><span data-stu-id="e52a4-103">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e52a4-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="e52a4-104">Overview</span></span>

<span data-ttu-id="e52a4-105">Mithilfe des Authentifizierungs-/Autorisierungsfeatures von Azure App Service kann Ihre Anwendung Benutzer anmelden, sodass Sie keine Codeänderungen für das Back-End der App vornehmen müssen.</span><span class="sxs-lookup"><span data-stu-id="e52a4-105">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="e52a4-106">Die Autorisierung stellt eine einfache Möglichkeit zum Schutz Ihrer Anwendung und für die Arbeit mit benutzerspezifischen Daten bereit.</span><span class="sxs-lookup"><span data-stu-id="e52a4-106">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="e52a4-107">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="e52a4-107">Management package</span></span>

<span data-ttu-id="e52a4-108">Installieren der Azure-Autorisierungsmodule für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="e52a4-108">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e52a4-109">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="e52a4-109">Install the npm module</span></span>

<span data-ttu-id="e52a4-110">Installieren des npm-Moduls für Azure-Autorisierung</span><span class="sxs-lookup"><span data-stu-id="e52a4-110">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="e52a4-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e52a4-111">Example</span></span>

<span data-ttu-id="e52a4-112">Mit diesem Beispiel werden alle Rollenzuweisungen für die angeforderte Ressourcengruppe aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="e52a4-112">This example lists all role assignments for the requested resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="e52a4-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="e52a4-113">Samples</span></span>

<span data-ttu-id="e52a4-114">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="e52a4-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
