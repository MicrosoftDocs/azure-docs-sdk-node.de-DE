---
title: "Azure-Ratgeber-Module für Node.js"
description: "Referenz zu Azure-Ratgeber-Modulen für Node.js"
keywords: Azure,SDK,API,Advisor, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 9d0b22cd5f164cb0b1bb79a2cda1aceba0187ba5
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-advisor-modules-for-nodejs"></a>Azure-Ratgeber-Module für Node.js

## <a name="overview"></a>Übersicht

Bei Azure Advisor handelt es sich um einen personalisierten Cloudberater, der Sie mit bewährten Methoden zum Optimieren von Azure-Bereitstellungen unterstützt. Ratgeber analysiert Ihre Ressourcenkonfiguration und Nutzungstelemetrie und macht anschließend Vorschläge zu Lösungen, die die Wirtschaftlichkeit, Leistung, Verfügbarkeit und Sicherheit Ihrer Azure-Ressourcen steigern können.

Der Ratgeber ermöglicht Folgendes:
- Abrufen proaktiver, umsetzbarer und individueller Empfehlungen und bewährter Methoden.
- Verbessern der Leistung, Sicherheit und Verfügbarkeit Ihrer Ressourcen und Ermitteln von Möglichkeiten der Senkung Ihrer Gesamtausgaben für Azure.
- Abrufen von Empfehlungen mit vorgeschlagenen Inlineaktionen.

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls für Azure-Ratgeber

```bash
npm install azure-arm-advisor
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel wird die Liste der Empfehlungen von Azure-Ratgeber angezeigt:

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a>Beispiele

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
