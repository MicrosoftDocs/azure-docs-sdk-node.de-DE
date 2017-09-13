---
title: "Azure Logic Apps-Module für Node.js"
description: "Referenz zu Azure Logic Apps-Modulen für Node.js"
keywords: Azure SDK, API, Logic Apps, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 70380dbf1fd199ba4909975b05ade72efaa4e0ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-logic-apps-modules-for-nodejs"></a>Azure Logic Apps-Module für Node.js

## <a name="overview"></a>Übersicht
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

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
