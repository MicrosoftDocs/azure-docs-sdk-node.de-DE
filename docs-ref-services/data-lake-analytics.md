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
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51381374"
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a>Azure Data Lake Analytics-Module für Node.js

Azure Data Lake Analytics ist ein bedarfsgesteuerter Dienst für Analyseaufträge zum Vereinfachen von Big Data-Analysen. Sie können sich auf das Schreiben, Ausführen und Verwalten von Aufträgen konzentrieren und müssen sich nicht mit dem Betrieb der verteilten Infrastruktur auseinandersetzen. Anstatt sich der Bereitstellung, Konfiguration und Optimierung von Hardware zu widmen, schreiben Sie Abfragen, mit denen Sie Ihre Daten transformieren und nützliche Einblicke erhalten. Der Analysedienst ist in der Lage, umgehend Aufträge jeglicher Größenordnung zu verarbeiten. Wählen Sie dazu die jeweils erforderliche Ressourcenkapazität aus. Da Sie nur für die Leistung bezahlen, die während der Ausführung Ihres Auftrags tatsächlich in Anspruch genommen wurde, ist dies eine überaus kosteneffektive Lösung. Durch die Unterstützung von Azure Active Directory kann Data Lake zur Verwaltung von Zugriffsberechtigungen und Rollen in Ihr lokales Identitätssystem integriert werden. Darüber hinaus umfasst dieser Dienst U-SQL, eine Sprache, bei der die Vorteile von SQL mit den Ausdrücken von Benutzercode kombiniert werden. Die skalierbare verteilte Laufzeit von U-SQL ermöglicht eine effiziente Analyse der Daten im Speicher sowie in SQL Server-Instanzen in Azure, Azure SQL-Datenbank und Azure SQL Data Warehouse.

### <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren der Azure Data Lake Analytics-Module für Node.js mithilfe von npm

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel werden alle Analytics-Konten für ein bestimmtes Abonnement aufgelistet:

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

## <a name="samples"></a>Beispiele

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
