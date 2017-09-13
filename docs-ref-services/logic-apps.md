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
# <a name="azure-logic-apps-modules-for-nodejs"></a><span data-ttu-id="580b7-104">Azure Logic Apps-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="580b7-104">Azure Logic Apps modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="580b7-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="580b7-105">Overview</span></span>
<span data-ttu-id="580b7-106">Logik-Apps ermöglichen die Vereinfachung und die Implementierung skalierbarer Integrationen und Workflows in die Cloud.</span><span class="sxs-lookup"><span data-stu-id="580b7-106">Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud.</span></span> <span data-ttu-id="580b7-107">Es wird ein visueller Designer bereitgestellt, mit dem Sie Ihre Prozesse in Form von Schritten (als Workflow bezeichnet) modellieren und automatisieren können.</span><span class="sxs-lookup"><span data-stu-id="580b7-107">It provides a visual designer to model and automate your process as a series of steps known as a workflow.</span></span> <span data-ttu-id="580b7-108">In der Cloud und der lokalen Umgebung sind viele Connectors zur schnellen Integration für Dienste und Protokolle enthalten.</span><span class="sxs-lookup"><span data-stu-id="580b7-108">There are many connectors across the cloud and on-premises to quickly integrate across services and protocols.</span></span> <span data-ttu-id="580b7-109">Eine Logik-App beginnt mit einem Trigger (z.B. „Wenn Dynamics CRM ein Konto hinzugefügt wird“), und nach der Auslösung sind viele verschiedene Kombinationen von Aktionen, Konvertierungen und Bedingungslogikabläufen möglich.</span><span class="sxs-lookup"><span data-stu-id="580b7-109">A logic app begins with a trigger (like 'When an account is added to Dynamics CRM') and after firing can begin many combinations of actions, conversions, and condition logic.</span></span>

<span data-ttu-id="580b7-110">Die Verwendung von Logik-Apps hat u.a. die folgenden Vorteile:</span><span class="sxs-lookup"><span data-stu-id="580b7-110">The advantages of using Logic Apps include the following:</span></span>
- <span data-ttu-id="580b7-111">Sparen von Zeit, indem komplexe Prozesse mit einfachen Designtools entworfen werden</span><span class="sxs-lookup"><span data-stu-id="580b7-111">Saving time by designing complex processes using easy to understand design tools</span></span>
- <span data-ttu-id="580b7-112">Nahtloses Implementieren von Mustern und Workflows, die andernfalls im Code nur schwer zu implementieren sind</span><span class="sxs-lookup"><span data-stu-id="580b7-112">Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code</span></span>
- <span data-ttu-id="580b7-113">Schnelles Starten mit Vorlagen</span><span class="sxs-lookup"><span data-stu-id="580b7-113">Getting started quickly from templates</span></span>
- <span data-ttu-id="580b7-114">Anpassen der Logik-App mit eigenen APIs, Codeelementen und Aktionen</span><span class="sxs-lookup"><span data-stu-id="580b7-114">Customizing your logic app with your own custom APIs, code, and actions</span></span>
- <span data-ttu-id="580b7-115">Herstellen einer Verbindung und Synchronisieren von unterschiedlichen Systemen in lokalen Umgebungen und der Cloud</span><span class="sxs-lookup"><span data-stu-id="580b7-115">Connect and synchronise disparate systems across on-premises and the cloud</span></span>
- <span data-ttu-id="580b7-116">Erstellen mit BizTalk Server, API Management, Azure Functions und Azure Service Bus mit erstklassiger Integrationsunterstützung</span><span class="sxs-lookup"><span data-stu-id="580b7-116">Build off of BizTalk server, API Management, Azure Functions, and Azure Service Bus with first-class integration support</span></span>

<span data-ttu-id="580b7-117">Bei Logik-Apps handelt es sich um einen vollständig verwalteten Dienst vom Typ „iPaaS“ (integration Platform as a Service), mit dem Entwickler sich keine Sorgen in Bezug auf Hosting, Skalierbarkeit, Verfügbarkeit und Verwaltung machen müssen.</span><span class="sxs-lookup"><span data-stu-id="580b7-117">Logic Apps is a fully managed iPaaS (integration Platform as a Service) allowing developers not to have to worry about building hosting, scalability, availability and management.</span></span> <span data-ttu-id="580b7-118">Logik-Apps werden automatisch zentral hochskaliert, um den Bedarf zu decken.</span><span class="sxs-lookup"><span data-stu-id="580b7-118">Logic Apps will scale up automatically to meet demand.</span></span>

## <a name="management-package"></a><span data-ttu-id="580b7-119">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="580b7-119">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="580b7-120">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="580b7-120">Install the npm module</span></span>

<span data-ttu-id="580b7-121">Installieren des Azure-Logikmoduls für Node.js</span><span class="sxs-lookup"><span data-stu-id="580b7-121">Install the Azure logic module for Node.js</span></span>

```bash
npm install azure-arm-logic
```

### <a name="example"></a><span data-ttu-id="580b7-122">Beispiel</span><span class="sxs-lookup"><span data-stu-id="580b7-122">Example</span></span>

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

### <a name="samples"></a><span data-ttu-id="580b7-123">Beispiele</span><span class="sxs-lookup"><span data-stu-id="580b7-123">Samples</span></span>

<span data-ttu-id="580b7-124">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="580b7-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
