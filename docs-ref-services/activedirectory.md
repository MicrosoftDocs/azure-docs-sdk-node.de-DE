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
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "51157889"
---
# <a name="azure-active-directory-modules-for-nodejs"></a>Azure Active Directory-Module für Node.js

## <a name="overview"></a>Übersicht

> [!IMPORTANT]
> Es wird dringend empfohlen, dass Sie [Microsoft Graph](https://graph.microsoft.io/) anstelle der Azure AD Graph-API für den Zugriff auf Azure Active Directory-Ressourcen verwenden. Unsere Entwicklungstätigkeiten konzentrieren sich nun auf Microsoft Graph, während für die Azure AD Graph-API keine weiteren Verbesserungen geplant sind. Die Szenarien, für die die Azure AD Graph-API möglicherweise weiterhin geeignet ist, ist nur sehr begrenzt. Weitere Informationen dazu finden Sie im Blogbeitrag [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) (Microsoft Graph oder Azure AD Graph) im Office Dev Center.

Mit der [Azure Active Directory Authentication Library (ADAL) für Node.js](https://www.npmjs.com/package/adal-node) können sich Node.js-Anwendungen bei AAD authentifizieren, um auf durch AAD geschützte Webressourcen zuzugreifen.

## <a name="client-package"></a>Clientpaket

### <a name="install-the-npm-modules"></a>Installieren der npm-Module

Verwenden Sie npm, um die Client- oder Verwaltungsmodule von Azure Storage zu installieren.

```bash
npm install adal-node
```   

### <a name="example"></a>Beispiel

Das folgende Beispiel aus dem [Beispiel mit Clientanmeldeinformationen](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) veranschaulicht die Server-zu-Server-Authentifizierung über Clientanmeldeinformationen.

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

## <a name="samples"></a>Beispiele

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
