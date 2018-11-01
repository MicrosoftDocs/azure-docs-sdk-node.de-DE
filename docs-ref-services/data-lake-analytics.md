---
title: Azure Data Lake Analytics-Module für Node.js
description: Referenz zu Azure Data Lake Analytics-Modulen für Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 97a846d9970310931e05e681b23b5787c97260b6
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50284226"
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a><span data-ttu-id="9fd48-103">Azure Data Lake Analytics-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="9fd48-103">Azure Data Lake Analytics modules for Node.js</span></span>

<span data-ttu-id="9fd48-104">Azure Data Lake Analytics ist ein bedarfsgesteuerter Dienst für Analyseaufträge zum Vereinfachen von Big Data-Analysen.</span><span class="sxs-lookup"><span data-stu-id="9fd48-104">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span> <span data-ttu-id="9fd48-105">Sie können sich auf das Schreiben, Ausführen und Verwalten von Aufträgen konzentrieren und müssen sich nicht mit dem Betrieb der verteilten Infrastruktur auseinandersetzen.</span><span class="sxs-lookup"><span data-stu-id="9fd48-105">You can focus on writing, running, and managing jobs rather than on operating distributed infrastructure.</span></span> <span data-ttu-id="9fd48-106">Anstatt sich der Bereitstellung, Konfiguration und Optimierung von Hardware zu widmen, schreiben Sie Abfragen, mit denen Sie Ihre Daten transformieren und nützliche Einblicke erhalten.</span><span class="sxs-lookup"><span data-stu-id="9fd48-106">Instead of deploying, configuring, and tuning hardware, you write queries to transform your data and extract valuable insights.</span></span> <span data-ttu-id="9fd48-107">Der Analysedienst ist in der Lage, umgehend Aufträge jeglicher Größenordnung zu verarbeiten. Wählen Sie dazu die jeweils erforderliche Ressourcenkapazität aus.</span><span class="sxs-lookup"><span data-stu-id="9fd48-107">The analytics service can handle jobs of any scale instantly by setting the dial for how much power you need.</span></span> <span data-ttu-id="9fd48-108">Da Sie nur für die Leistung bezahlen, die während der Ausführung Ihres Auftrags tatsächlich in Anspruch genommen wurde, ist dies eine überaus kosteneffektive Lösung.</span><span class="sxs-lookup"><span data-stu-id="9fd48-108">You only pay for your job when it is running, making it cost-effective.</span></span> <span data-ttu-id="9fd48-109">Durch die Unterstützung von Azure Active Directory kann Data Lake zur Verwaltung von Zugriffsberechtigungen und Rollen in Ihr lokales Identitätssystem integriert werden.</span><span class="sxs-lookup"><span data-stu-id="9fd48-109">The analytics service supports Azure Active Directory letting you manage access and roles, integrated with your on-premises identity system.</span></span> <span data-ttu-id="9fd48-110">Darüber hinaus umfasst dieser Dienst U-SQL, eine Sprache, bei der die Vorteile von SQL mit den Ausdrücken von Benutzercode kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="9fd48-110">It also includes U-SQL, a language that unifies the benefits of SQL with the expressive power of user code.</span></span> <span data-ttu-id="9fd48-111">Die skalierbare verteilte Laufzeit von U-SQL ermöglicht eine effiziente Analyse der Daten im Speicher sowie in SQL Server-Instanzen in Azure, Azure SQL-Datenbank und Azure SQL Data Warehouse.</span><span class="sxs-lookup"><span data-stu-id="9fd48-111">U-SQL’s scalable distributed runtime enables you to efficiently analyze data in the store and across SQL Servers in Azure, Azure SQL Database, and Azure SQL Data Warehouse.</span></span>

### <a name="management-package"></a><span data-ttu-id="9fd48-112">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="9fd48-112">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9fd48-113">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="9fd48-113">Install the npm module</span></span>

<span data-ttu-id="9fd48-114">Installieren der Azure Data Lake Analytics-Module für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="9fd48-114">Use npm to install the Azure Data Lake Analytics modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a><span data-ttu-id="9fd48-115">Beispiel</span><span class="sxs-lookup"><span data-stu-id="9fd48-115">Example</span></span>

<span data-ttu-id="9fd48-116">Mit diesem Beispiel werden alle Analytics-Konten für ein bestimmtes Abonnement aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="9fd48-116">This example lists all of the analytics accounts for a given subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-analytics');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeAnalyticsAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a><span data-ttu-id="9fd48-117">Beispiele</span><span class="sxs-lookup"><span data-stu-id="9fd48-117">Samples</span></span>

<span data-ttu-id="9fd48-118">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="9fd48-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
