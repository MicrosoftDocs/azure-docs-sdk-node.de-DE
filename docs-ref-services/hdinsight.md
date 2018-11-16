---
title: Azure HDInsight-Module für Node.js
description: Referenz zu Azure HDInsight-Modulen für Node.js
ms.service: hdinsight
author: jasonwhowell
ms.author: jasonh
manager: kfile
ms.topic: article
ms.devlang: nodejs
ms.date: 07/18/2017
ms.openlocfilehash: e35e0d487efce2a591130403f8b72a43c638fdec
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51395644"
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="f3014-103">Azure HDInsight-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="f3014-103">Azure HDInsight Modules for Node.js</span></span>

<span data-ttu-id="f3014-104">Azure HDInsight ist eine Clouddistribution der Hadoop-Komponenten von Hortonworks Data Platform (HDP).</span><span class="sxs-lookup"><span data-stu-id="f3014-104">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="f3014-105">Apache Hadoop war ursprünglich ein Open Source-Framework für die verteilte Verarbeitung und Analyse großer Datasets in Clustern von Computern.</span><span class="sxs-lookup"><span data-stu-id="f3014-105">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="f3014-106">Mit HDInsight bieten Hadoop-Technologien folgende Vorteile für die Nutzung:</span><span class="sxs-lookup"><span data-stu-id="f3014-106">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="f3014-107">Weniger Setup- und Konfigurationsaufwand.</span><span class="sxs-lookup"><span data-stu-id="f3014-107">Less setup and configuration.</span></span> <span data-ttu-id="f3014-108">Siehe „Bereitstellen von Hadoop-Clustern in HDInsight“.</span><span class="sxs-lookup"><span data-stu-id="f3014-108">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="f3014-109">Hochverfügbarkeit und Zuverlässigkeit.</span><span class="sxs-lookup"><span data-stu-id="f3014-109">High availability and reliability.</span></span> <span data-ttu-id="f3014-110">Siehe „Verfügbarkeit und Zuverlässigkeit von HDInsight“.</span><span class="sxs-lookup"><span data-stu-id="f3014-110">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="f3014-111">Sicherheit und Governance über die Active Directory-Integration.</span><span class="sxs-lookup"><span data-stu-id="f3014-111">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="f3014-112">Siehe „In Domänen eingebundene Cluster“.</span><span class="sxs-lookup"><span data-stu-id="f3014-112">See Domain-joined clusters.</span></span>
- <span data-ttu-id="f3014-113">Dynamisches Skalieren ohne Unterbrechung von Aufträgen</span><span class="sxs-lookup"><span data-stu-id="f3014-113">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="f3014-114">Komponentenupdates und aktuelle Versionen.</span><span class="sxs-lookup"><span data-stu-id="f3014-114">Component updates and current versions.</span></span> <span data-ttu-id="f3014-115">Siehe „Hadoop-Komponenten und -Versionen in HDInsight“.</span><span class="sxs-lookup"><span data-stu-id="f3014-115">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="f3014-116">Integration in andere Azure-Dienste wie Web-Apps und SQL-Datenbank</span><span class="sxs-lookup"><span data-stu-id="f3014-116">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="f3014-117">Der Hadoop-Technologiestapel umfasst verwandte Software und Hilfsprogramme, einschließlich Apache Hive, HBase, Spark, Kafka und viele andere.</span><span class="sxs-lookup"><span data-stu-id="f3014-117">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="f3014-118">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="f3014-118">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="f3014-119">Installieren der npm-Module</span><span class="sxs-lookup"><span data-stu-id="f3014-119">Install the npm modules</span></span>

<span data-ttu-id="f3014-120">Installieren der Azure HDInsight-Module für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="f3014-120">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="f3014-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f3014-121">Example</span></span> 

<span data-ttu-id="f3014-122">Mit diesem Beispiel wird ein HDInsight-Client erstellt, und anschließend werden alle verfügbaren Cluster aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="f3014-122">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

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

## <a name="samples"></a><span data-ttu-id="f3014-123">Beispiele</span><span class="sxs-lookup"><span data-stu-id="f3014-123">Samples</span></span>

<span data-ttu-id="f3014-124">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="f3014-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
