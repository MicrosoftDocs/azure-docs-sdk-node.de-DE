---
title: "Azure HDInsight-Module für Node.js"
description: "Referenz zu Azure HDInsight-Modulen für Node.js"
keywords: Azure,SDK,API,HDInsight, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 1df988e98def42dcf33e90b4c3debece8cbe85e3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="46277-104">Azure HDInsight-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="46277-104">Azure HDInsight Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="46277-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="46277-105">Overview</span></span>

<span data-ttu-id="46277-106">Azure HDInsight ist eine Clouddistribution der Hadoop-Komponenten von Hortonworks Data Platform (HDP).</span><span class="sxs-lookup"><span data-stu-id="46277-106">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="46277-107">Apache Hadoop war ursprünglich ein Open Source-Framework für die verteilte Verarbeitung und Analyse großer Datasets in Clustern von Computern.</span><span class="sxs-lookup"><span data-stu-id="46277-107">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="46277-108">Mit HDInsight bieten Hadoop-Technologien folgende Vorteile für die Nutzung:</span><span class="sxs-lookup"><span data-stu-id="46277-108">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="46277-109">Weniger Setup- und Konfigurationsaufwand.</span><span class="sxs-lookup"><span data-stu-id="46277-109">Less setup and configuration.</span></span> <span data-ttu-id="46277-110">Siehe „Bereitstellen von Hadoop-Clustern in HDInsight“.</span><span class="sxs-lookup"><span data-stu-id="46277-110">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="46277-111">Hohe Verfügbarkeit und Zuverlässigkeit.</span><span class="sxs-lookup"><span data-stu-id="46277-111">High availability and reliability.</span></span> <span data-ttu-id="46277-112">Siehe „Verfügbarkeit und Zuverlässigkeit von HDInsight“.</span><span class="sxs-lookup"><span data-stu-id="46277-112">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="46277-113">Sicherheit und Governance über die Active Directory-Integration.</span><span class="sxs-lookup"><span data-stu-id="46277-113">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="46277-114">Siehe „In Domänen eingebundene Cluster“.</span><span class="sxs-lookup"><span data-stu-id="46277-114">See Domain-joined clusters.</span></span>
- <span data-ttu-id="46277-115">Dynamisches Skalieren ohne Unterbrechung von Aufträgen</span><span class="sxs-lookup"><span data-stu-id="46277-115">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="46277-116">Komponentenupdates und aktuelle Versionen.</span><span class="sxs-lookup"><span data-stu-id="46277-116">Component updates and current versions.</span></span> <span data-ttu-id="46277-117">Siehe „Hadoop-Komponenten und -Versionen in HDInsight“.</span><span class="sxs-lookup"><span data-stu-id="46277-117">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="46277-118">Integration in andere Azure-Dienste wie Web-Apps und SQL-Datenbank</span><span class="sxs-lookup"><span data-stu-id="46277-118">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="46277-119">Der Hadoop-Technologiestapel umfasst verwandte Software und Hilfsprogramme, einschließlich Apache Hive, HBase, Spark, Kafka und viele andere.</span><span class="sxs-lookup"><span data-stu-id="46277-119">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="46277-120">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="46277-120">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="46277-121">Installieren der npm-Module</span><span class="sxs-lookup"><span data-stu-id="46277-121">Install the npm modules</span></span>

<span data-ttu-id="46277-122">Installieren der Azure HDInsight-Module für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="46277-122">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="46277-123">Beispiel</span><span class="sxs-lookup"><span data-stu-id="46277-123">Example</span></span> 

<span data-ttu-id="46277-124">Mit diesem Beispiel wird ein HDInsight-Client erstellt, und anschließend werden alle verfügbaren Cluster aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="46277-124">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

```javascript
const msRestAzure = require('ms-rest-azure');
const HDInsightManagementClient = require('azure-arm-hdinsight');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = HDInsightManagementClient.createHDInsightManagementClient(
        credentials
    );

    credentials.subscriptionId = subscriptionId;

    client.clusters.list((err, result) => {
        console.log(result);
    });
});
```

## <a name="samples"></a><span data-ttu-id="46277-125">Beispiele</span><span class="sxs-lookup"><span data-stu-id="46277-125">Samples</span></span>

<span data-ttu-id="46277-126">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="46277-126">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
