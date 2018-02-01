---
title: "Azure Advisor-Module für Node.js"
description: "Referenz zu Azure Advisor-Modulen für Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: aad3b292c6304159f68a81270e671cd335c972ec
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2018
---
# <a name="azure-advisor-modules-for-nodejs"></a>Azure Advisor-Module für Node.js

## <a name="overview"></a>Übersicht

Bei Azure Advisor handelt es sich um einen personalisierten Cloudberater, der Sie mit bewährten Methoden zum Optimieren von Azure-Bereitstellungen unterstützt. Der Advisor analysiert Ihre Ressourcenkonfiguration und Nutzungstelemetrie und macht anschließend Vorschläge zu Lösungen, die die Wirtschaftlichkeit, Leistung, Hochverfügbarkeit und Sicherheit Ihrer Azure-Ressourcen steigern können.

Der Advisor ermöglicht Folgendes:
- Abrufen proaktiver, umsetzbarer und individueller Empfehlungen und bewährter Methoden.
- Verbessern der Leistung, Sicherheit und Hochverfügbarkeit Ihrer Ressourcen und Ermitteln von Möglichkeiten der Senkung Ihrer Gesamtausgaben für Azure.
- Abrufen von Empfehlungen mit vorgeschlagenen Inlineaktionen.

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls für den Azure Advisor

```bash
npm install azure-arm-advisor
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel wird die Liste der Empfehlungen von Azure Advisor angezeigt:

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

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
