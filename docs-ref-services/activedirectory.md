---
title: "Azure Active Directory-Module für Node.js"
description: "Referenz zu Azure Active Directory-Modulen für Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: 59ef5321db6e5e7f3ad0e3b63aaa6a107207d3c2
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2018
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="5e6ea-103">Azure Active Directory-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="5e6ea-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="5e6ea-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="5e6ea-104">Overview</span></span>

<span data-ttu-id="5e6ea-105">Mit der [Azure Active Directory Authentication Library (ADAL) für Node.js](https://www.npmjs.com/package/adal-node) können sich Node.js-Anwendungen bei AAD authentifizieren, um auf durch AAD geschützte Webressourcen zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="5e6ea-105">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="5e6ea-106">Clientpaket</span><span class="sxs-lookup"><span data-stu-id="5e6ea-106">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="5e6ea-107">Installieren der npm-Module</span><span class="sxs-lookup"><span data-stu-id="5e6ea-107">Install the npm modules</span></span>

<span data-ttu-id="5e6ea-108">Verwenden Sie npm, um die Client- oder Verwaltungsmodule von Azure Storage zu installieren.</span><span class="sxs-lookup"><span data-stu-id="5e6ea-108">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="5e6ea-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5e6ea-109">Example</span></span>

<span data-ttu-id="5e6ea-110">Das folgende Beispiel aus dem [Beispiel mit Clientanmeldeinformationen](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) veranschaulicht die Server-zu-Server-Authentifizierung über Clientanmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="5e6ea-110">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

```javascript
const adal = require('adal-node').AuthenticationContext;

const authorityHostUrl = 'https://login.windows.net';
const tenant = 'your-tenant-id';
const authorityUrl = authorityHostUrl + '/' + tenant;
const clientId = 'your-client-id';
const clientSecret = 'your-client-secret';
const resource = 'your-app-id-uri';

const context = new adal(authorityUrl);

context.acquireTokenWithClientCredentials(
  resource,
  clientId,
  clientSecret,
  (err, tokenResponse) => {
    if (err) {
      console.log(`Token generation failed due to ${err}`);
    } else {
      console.dir(tokenResponse, { depth: null, colors: true });
    }
  }
);
```

## <a name="samples"></a><span data-ttu-id="5e6ea-111">Beispiele</span><span class="sxs-lookup"><span data-stu-id="5e6ea-111">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="5e6ea-112">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="5e6ea-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
