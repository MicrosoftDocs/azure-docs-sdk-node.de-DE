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
# <a name="azure-active-directory-modules-for-nodejs"></a>Azure Active Directory-Module für Node.js

## <a name="overview"></a>Übersicht

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
