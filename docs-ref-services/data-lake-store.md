---
title: "Azure Data Lake Store-Module für Node.js"
description: "Referenz zu Azure Data Lake Store-Modulen für Node.js"
keywords: Azure,SDK,API,Data Lake Store, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: 5885bf8f073e4f4f1ac2be88b8691b092e8a21d3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a>Azure Data Lake Store-Module für Node.js

## <a name="overview"></a>Übersicht
Azure Data Lake-Speicher ist ein unternehmensweites riesiges Repository für Big Data-Analyseworkloads. Azure Data Lake bietet Ihnen die Möglichkeit, Daten von beliebiger Größe, Art und Erfassungsgeschwindigkeit zur Durchführung operativer und explorativer Analysen an einem einzigen Ort zu erfassen.

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren der Azure Data Lake Store-Module für Node.js mithilfe von npm

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel werden alle Data Lake Store-Konten innerhalb eines bestimmten Azure-Abonnements aufgelistet:

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-store');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeStoreAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a>Beispiele

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
