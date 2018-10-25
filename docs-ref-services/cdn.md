---
title: Azure CDN-Module für Node.js
description: Referenz zu anderen Azure CDN-Modulen für Node.js
author: dksimpson
ms.author: v-deasim
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: 1117f8fabfe364d3e5602ee89f652fe98851fef4
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "49661085"
---
# <a name="azure-cdn-modules-for-nodejs"></a><span data-ttu-id="2830f-103">Azure CDN-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="2830f-103">Azure CDN modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2830f-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="2830f-104">Overview</span></span>

<span data-ttu-id="2830f-105">Das Azure Content Delivery Network (CDN) bietet Entwicklern eine globale Lösung für die Bereitstellung von Inhalten mit hoher Bandbreite, die in Azure oder an einem beliebigen anderen Ort gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="2830f-105">The Azure Content Delivery Network (CDN) offers developers a global solution for delivering high-bandwidth content that is hosted in Azure or any other location.</span></span> <span data-ttu-id="2830f-106">Mit einem CDN können Sie öffentlich verfügbare Objekte zwischenspeichern, die aus Azure Blob Storage, einer Webanwendung, einem virtuellen Computer, einem Anwendungsordner oder einem anderen HTTP-/HTTPS-Speicherort geladen werden.</span><span class="sxs-lookup"><span data-stu-id="2830f-106">Using the CDN, you can cache publicly available objects loaded from Azure blob storage, a web application, virtual machine, application folder, or other HTTP/HTTPS location.</span></span> <span data-ttu-id="2830f-107">Der zum Zwischenspeichern verwendete CDN-Cache kann an strategischen Standorten angesiedelt werden, um beim Übermitteln des Inhalts an die Benutzer eine maximale Bandbreite zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="2830f-107">The CDN cache can be held at strategic locations to provide maximum bandwidth for delivering content to users.</span></span> <span data-ttu-id="2830f-108">Ein CDN wird normalerweise zum Bereitstellen statischer Inhalte wie Bilder, Stylesheets, Dokumente, Dateien, clientseitige Skripts und HTML-Seiten verwendet.</span><span class="sxs-lookup"><span data-stu-id="2830f-108">The CDN is typically used for delivering static content such as images, style sheets, documents, files, client-side scripts, and HTML pages.</span></span>

## <a name="management-package"></a><span data-ttu-id="2830f-109">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="2830f-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2830f-110">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="2830f-110">Install the npm module</span></span>

<span data-ttu-id="2830f-111">Installieren des npm-Moduls für Azure CDN</span><span class="sxs-lookup"><span data-stu-id="2830f-111">Install the Azure CDN npm module</span></span>

```bash
npm install azure-arm-cdn
```

### <a name="example"></a><span data-ttu-id="2830f-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2830f-112">Example</span></span>

<span data-ttu-id="2830f-113">Mit diesem Beispiel werden CDN-Profile aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="2830f-113">This example lists all of the CDN profiles.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a><span data-ttu-id="2830f-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="2830f-114">Samples</span></span>

<span data-ttu-id="2830f-115">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="2830f-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
