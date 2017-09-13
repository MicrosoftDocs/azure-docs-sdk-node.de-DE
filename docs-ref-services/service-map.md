---
title: "Azure-Dienstzuordnungsmodule für Node.js"
description: "Referenz zu Azure-Dienstzuordnungsmodulen für Node.js"
keywords: Azure,SDK,API,Dienstzuordnung, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 330cbceb07ba8bea65c1059a1edb3cd9c69653bc
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-map-modules-for-nodejs"></a>Azure-Dienstzuordnungsmodule für Node.js

## <a name="overview"></a>Übersicht

Service Map ermittelt automatisch Anwendungskomponenten auf Windows- und Linux-Systemen und stellt die Kommunikation zwischen Diensten dar. Service Map zeigt Verbindungen zwischen Servern, Prozessen und Ports über die gesamte TCP-Verbindungsarchitektur an. Außer der Installation eines Agents ist keine weitere Konfiguration erforderlich.

Weitere Informationen zur [Azure-Dienstzuordnung](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map)

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls für die Azure-Dienstzuordnung

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel werden alle Dienstzuordnungen für die angegebene Ressourcengruppe und den angegebenen Arbeitsbereich aufgelistet:

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a>Beispiele

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
