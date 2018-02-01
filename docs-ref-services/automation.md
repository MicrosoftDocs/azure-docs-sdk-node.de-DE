---
title: "Azure Automation-Module für Node.js"
description: "Referenz zu Azure Automation-Modulen für Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 09e9d2675d49b29881d332e7bbf251a5031e3483
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2018
---
# <a name="azure-automation-modules-for-nodejs"></a>Azure Automation-Module für Node.js

## <a name="overview"></a>Übersicht

Azure Automation ermöglicht es Benutzern, die manuellen, längeren, fehleranfälligen und häufig wiederholten Aufgaben zu automatisieren, die in einer Cloud- und Unternehmensumgebung normalerweise ausgeführt werden. Automation spart Zeit, erhöht die Zuverlässigkeit normaler Verwaltungsaufgaben und plant diese sogar so ein, dass sie in regelmäßigen Abständen automatisch ausgeführt werden. Sie können Prozesse mit Runbooks automatisieren oder die Konfigurationsverwaltung über die Konfiguration für den gewünschten Zustand automatisieren.

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-modules-with-npm"></a>Installieren der Module mit npm

Installieren der Azure Automation-Module für Node.js mithilfe von npm

```bash
npm install azure-arm-automation
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel werden die Automation-Konten aufgeführt:

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));

```

## <a name="samples"></a>Beispiele

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
