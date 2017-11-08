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
# <a name="azure-hdinsight-modules-for-nodejs"></a>Azure HDInsight-Module für Node.js

## <a name="overview"></a>Übersicht

Azure HDInsight ist eine Clouddistribution der Hadoop-Komponenten von Hortonworks Data Platform (HDP). Apache Hadoop war ursprünglich ein Open Source-Framework für die verteilte Verarbeitung und Analyse großer Datasets in Clustern von Computern.

Mit HDInsight bieten Hadoop-Technologien folgende Vorteile für die Nutzung:
- Weniger Setup- und Konfigurationsaufwand. Siehe „Bereitstellen von Hadoop-Clustern in HDInsight“.
- Hohe Verfügbarkeit und Zuverlässigkeit. Siehe „Verfügbarkeit und Zuverlässigkeit von HDInsight“.
- Sicherheit und Governance über die Active Directory-Integration. Siehe „In Domänen eingebundene Cluster“.
- Dynamisches Skalieren ohne Unterbrechung von Aufträgen
- Komponentenupdates und aktuelle Versionen. Siehe „Hadoop-Komponenten und -Versionen in HDInsight“.
- Integration in andere Azure-Dienste wie Web-Apps und SQL-Datenbank

Der Hadoop-Technologiestapel umfasst verwandte Software und Hilfsprogramme, einschließlich Apache Hive, HBase, Spark, Kafka und viele andere. 

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-modules"></a>Installieren der npm-Module

Installieren der Azure HDInsight-Module für Node.js mithilfe von npm

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a>Beispiel 

Mit diesem Beispiel wird ein HDInsight-Client erstellt, und anschließend werden alle verfügbaren Cluster aufgelistet. 

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

## <a name="samples"></a>Beispiele

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.