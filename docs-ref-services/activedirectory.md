---
title: Azure Active Directory-Module für Node.js
description: Referenz zu Azure Active Directory-Modulen für Node.js
author: celestedg
ms.author: celested
manager: mtillman
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.openlocfilehash: 1189bf084fc7d77a1e5eed7f01f2f9bee2295b45
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2018
ms.locfileid: "52060255"
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="d8f5b-103">Azure Active Directory-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="d8f5b-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d8f5b-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="d8f5b-104">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8f5b-105">Es wird dringend empfohlen, dass Sie [Microsoft Graph](https://graph.microsoft.io/) anstelle der Azure AD Graph-API für den Zugriff auf Azure Active Directory-Ressourcen verwenden.</span><span class="sxs-lookup"><span data-stu-id="d8f5b-105">We strongly recommend that you use [Microsoft Graph](https://graph.microsoft.io/) instead of Azure AD Graph API to access Azure Active Directory resources.</span></span> <span data-ttu-id="d8f5b-106">Unsere Entwicklungstätigkeiten konzentrieren sich nun auf Microsoft Graph, während für die Azure AD Graph-API keine weiteren Verbesserungen geplant sind.</span><span class="sxs-lookup"><span data-stu-id="d8f5b-106">Our development efforts are now concentrated on Microsoft Graph and no further enhancements are planned for Azure AD Graph API.</span></span> <span data-ttu-id="d8f5b-107">Die Szenarien, für die die Azure AD Graph-API möglicherweise weiterhin geeignet ist, ist nur sehr begrenzt. Weitere Informationen dazu finden Sie im Blogbeitrag [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) (Microsoft Graph oder Azure AD Graph) im Office Dev Center.</span><span class="sxs-lookup"><span data-stu-id="d8f5b-107">There are a very limited number of scenarios for which Azure AD Graph API might still be appropriate; for more information, see the [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) blog post in the Office Dev Center.</span></span>

<span data-ttu-id="d8f5b-108">Mit der [Azure Active Directory Authentication Library (ADAL) für Node.js](https://www.npmjs.com/package/adal-node) können sich Node.js-Anwendungen bei AAD authentifizieren, um auf durch AAD geschützte Webressourcen zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="d8f5b-108">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="d8f5b-109">Clientpaket</span><span class="sxs-lookup"><span data-stu-id="d8f5b-109">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="d8f5b-110">Installieren der npm-Module</span><span class="sxs-lookup"><span data-stu-id="d8f5b-110">Install the npm modules</span></span>

<span data-ttu-id="d8f5b-111">Verwenden Sie npm, um die Client- oder Verwaltungsmodule von Azure Storage zu installieren.</span><span class="sxs-lookup"><span data-stu-id="d8f5b-111">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="d8f5b-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d8f5b-112">Example</span></span>

<span data-ttu-id="d8f5b-113">Das folgende Beispiel aus dem [Beispiel mit Clientanmeldeinformationen](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) veranschaulicht die Server-zu-Server-Authentifizierung über Clientanmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="d8f5b-113">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="d8f5b-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="d8f5b-114">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="d8f5b-115">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d8f5b-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
