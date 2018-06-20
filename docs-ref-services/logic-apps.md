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
ms.openlocfilehash: 2de867fdd0aa31b63b9680cc3f0c2e7f6301e632
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261551"
---
# <a name="azure-logic-apps-modules-for-nodejs"></a><span data-ttu-id="b51a5-103">Azure Logic Apps-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="b51a5-103">Azure Logic Apps modules for Node.js</span></span>

<span data-ttu-id="b51a5-104">Logik-Apps ermöglichen die Vereinfachung und die Implementierung skalierbarer Integrationen und Workflows in die Cloud.</span><span class="sxs-lookup"><span data-stu-id="b51a5-104">Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud.</span></span> <span data-ttu-id="b51a5-105">Es wird ein visueller Designer bereitgestellt, mit dem Sie Ihre Prozesse in Form von Schritten (als Workflow bezeichnet) modellieren und automatisieren können.</span><span class="sxs-lookup"><span data-stu-id="b51a5-105">It provides a visual designer to model and automate your process as a series of steps known as a workflow.</span></span> <span data-ttu-id="b51a5-106">In der Cloud und der lokalen Umgebung sind viele Connectors zur schnellen Integration für Dienste und Protokolle enthalten.</span><span class="sxs-lookup"><span data-stu-id="b51a5-106">There are many connectors across the cloud and on-premises to quickly integrate across services and protocols.</span></span> <span data-ttu-id="b51a5-107">Eine Logik-App beginnt mit einem Trigger (z.B. „Wenn Dynamics CRM ein Konto hinzugefügt wird“), und nach der Auslösung sind viele verschiedene Kombinationen von Aktionen, Konvertierungen und Bedingungslogikabläufen möglich.</span><span class="sxs-lookup"><span data-stu-id="b51a5-107">A logic app begins with a trigger (like 'When an account is added to Dynamics CRM') and after firing can begin many combinations of actions, conversions, and condition logic.</span></span>

<span data-ttu-id="b51a5-108">Die Verwendung von Logik-Apps hat u.a. die folgenden Vorteile:</span><span class="sxs-lookup"><span data-stu-id="b51a5-108">The advantages of using Logic Apps include the following:</span></span>
- <span data-ttu-id="b51a5-109">Sparen von Zeit, indem komplexe Prozesse mit einfachen Designtools entworfen werden</span><span class="sxs-lookup"><span data-stu-id="b51a5-109">Saving time by designing complex processes using easy to understand design tools</span></span>
- <span data-ttu-id="b51a5-110">Nahtloses Implementieren von Mustern und Workflows, die andernfalls im Code nur schwer zu implementieren sind</span><span class="sxs-lookup"><span data-stu-id="b51a5-110">Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code</span></span>
- <span data-ttu-id="b51a5-111">Schnelles Starten mit Vorlagen</span><span class="sxs-lookup"><span data-stu-id="b51a5-111">Getting started quickly from templates</span></span>
- <span data-ttu-id="b51a5-112">Anpassen der Logik-App mit eigenen APIs, Codeelementen und Aktionen</span><span class="sxs-lookup"><span data-stu-id="b51a5-112">Customizing your logic app with your own custom APIs, code, and actions</span></span>
- <span data-ttu-id="b51a5-113">Herstellen einer Verbindung und Synchronisieren von unterschiedlichen Systemen in lokalen Umgebungen und der Cloud</span><span class="sxs-lookup"><span data-stu-id="b51a5-113">Connect and synchronise disparate systems across on-premises and the cloud</span></span>
- <span data-ttu-id="b51a5-114">Erstellen mit BizTalk Server, API Management, Azure Functions und Azure Service Bus mit erstklassiger Integrationsunterstützung</span><span class="sxs-lookup"><span data-stu-id="b51a5-114">Build off of BizTalk server, API Management, Azure Functions, and Azure Service Bus with first-class integration support</span></span>

<span data-ttu-id="b51a5-115">Bei Logik-Apps handelt es sich um einen vollständig verwalteten Dienst vom Typ „iPaaS“ (integration Platform as a Service), mit dem Entwickler sich keine Sorgen in Bezug auf Hosting, Skalierbarkeit, Verfügbarkeit und Verwaltung machen müssen.</span><span class="sxs-lookup"><span data-stu-id="b51a5-115">Logic Apps is a fully managed iPaaS (integration Platform as a Service) allowing developers not to have to worry about building hosting, scalability, availability and management.</span></span> <span data-ttu-id="b51a5-116">Logik-Apps werden automatisch zentral hochskaliert, um den Bedarf zu decken.</span><span class="sxs-lookup"><span data-stu-id="b51a5-116">Logic Apps will scale up automatically to meet demand.</span></span>

## <a name="management-package"></a><span data-ttu-id="b51a5-117">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="b51a5-117">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b51a5-118">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="b51a5-118">Install the npm module</span></span>

<span data-ttu-id="b51a5-119">Installieren des Azure-Logikmoduls für Node.js</span><span class="sxs-lookup"><span data-stu-id="b51a5-119">Install the Azure logic module for Node.js</span></span>

```bash
npm install azure-arm-logic
```

### <a name="example"></a><span data-ttu-id="b51a5-120">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b51a5-120">Example</span></span>

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

### <a name="samples"></a><span data-ttu-id="b51a5-121">Beispiele</span><span class="sxs-lookup"><span data-stu-id="b51a5-121">Samples</span></span>

<span data-ttu-id="b51a5-122">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="b51a5-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
