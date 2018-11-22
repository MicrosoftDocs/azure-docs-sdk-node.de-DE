---
title: Azure Logic Apps-Module für Node.js
description: Referenz zu Azure Logic Apps-Modulen für Node.js
author: ecfan
ms.author: estfan
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 021f57c7f4f1b86a3c0e97f345d2f934351669b8
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2018
ms.locfileid: "52132365"
---
# <a name="azure-logic-apps-modules-for-nodejs"></a>Azure Logic Apps-Module für Node.js

Logik-Apps ermöglichen die Vereinfachung und die Implementierung skalierbarer Integrationen und Workflows in die Cloud. Es wird ein visueller Designer bereitgestellt, mit dem Sie Ihre Prozesse in Form von Schritten (als Workflow bezeichnet) modellieren und automatisieren können. In der Cloud und der lokalen Umgebung sind viele Connectors zur schnellen Integration für Dienste und Protokolle enthalten. Eine Logik-App beginnt mit einem Trigger (z.B. „Wenn Dynamics CRM ein Konto hinzugefügt wird“), und nach der Auslösung sind viele verschiedene Kombinationen von Aktionen, Konvertierungen und Bedingungslogikabläufen möglich.

Die Verwendung von Logik-Apps hat u.a. die folgenden Vorteile:
- Sparen von Zeit, indem komplexe Prozesse mit einfachen Designtools entworfen werden
- Nahtloses Implementieren von Mustern und Workflows, die andernfalls im Code nur schwer zu implementieren sind
- Schnelles Starten mit Vorlagen
- Anpassen der Logik-App mit eigenen APIs, Codeelementen und Aktionen
- Herstellen einer Verbindung und Synchronisieren von unterschiedlichen Systemen in lokalen Umgebungen und der Cloud
- Erstellen mit BizTalk Server, API Management, Azure Functions und Azure Service Bus mit erstklassiger Integrationsunterstützung

Bei Logik-Apps handelt es sich um einen vollständig verwalteten Dienst vom Typ „iPaaS“ (integration Platform as a Service), mit dem Entwickler sich keine Sorgen in Bezug auf Hosting, Skalierbarkeit, Verfügbarkeit und Verwaltung machen müssen. Logik-Apps werden automatisch zentral hochskaliert, um den Bedarf zu decken.

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des Azure-Logikmoduls für Node.js

```bash
npm install azure-arm-logic
```

### <a name="example"></a>Beispiel

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a>Beispiele

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
