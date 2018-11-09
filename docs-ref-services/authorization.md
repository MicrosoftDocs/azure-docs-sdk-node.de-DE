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
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "51062029"
---
# <a name="azure-authorization-modules-for-nodejs"></a>Azure-Autorisierungsmodule für Node.js

## <a name="overview"></a>Übersicht

Mithilfe des Authentifizierungs-/Autorisierungsfeatures von Azure App Service kann Ihre Anwendung Benutzer anmelden, sodass Sie keine Codeänderungen für das Back-End der App vornehmen müssen. Die Autorisierung stellt eine einfache Möglichkeit zum Schutz Ihrer Anwendung und für die Arbeit mit benutzerspezifischen Daten bereit.

## <a name="management-package"></a>Verwaltungspaket

Installieren der Azure-Autorisierungsmodule für Node.js mithilfe von npm

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls für Azure-Autorisierung

```bash
npm install azure-arm-authorization
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel werden alle Rollenzuweisungen für die angeforderte Ressourcengruppe aufgelistet:

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

## <a name="samples"></a>Beispiele

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
