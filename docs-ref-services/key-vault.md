---
title: "Azure Key Vault-Module für Node.js"
description: "Referenz zu Azure Key Vault-Modulen für Node.js"
keywords: Azure,SDK,API,Key Vault, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Key Vault
ms.openlocfilehash: e497e1e0e369dfd975fe5a2d7759ec893fbf6aff
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-key-vault-modules-for-nodejs"></a>Azure Key Vault-Module für Node.js

## <a name="overview"></a>Übersicht

Der Azure-Schlüsseltresor unterstützt Sie dabei, kryptografische Schlüssel und geheime Schlüssel zu schützen, die von Cloudanwendungen und -diensten verwendet werden. Durch Verwenden von Key Vault können Sie Schlüssel und Geheimnisse (beispielsweise Authentifizierungsschlüssel, Schlüssel für Speicherkonten, Datenverschlüsselungsschlüssel, PFX-Dateien und Kennwörter) verschlüsseln, indem Sie Schlüssel verwenden, die durch Hardwaresicherheitsmodule (HSMs) geschützt werden. Zur Steigerung der Sicherheit können Sie Schlüssel in HSMs importieren oder in diesen generieren. Bei Verwendung dieser Option verarbeitet Microsoft Ihre Schlüssel in mit FIPS 140-2 (Level 2) überprüften HSMs (Hardware und Firmware).

Der Schlüsseltresor optimiert die Schlüsselverwaltung und ermöglicht es Ihnen, die Kontrolle über Schlüssel zu behalten, die für den Datenzugriff und die Verschlüsselung Ihrer Daten verwendet werden. Entwickler können Schlüssel für Tests und Entwicklung innerhalb von Minuten erstellen und diese später nahtlos in Schlüssel für die Produktion migrieren. Sicherheitsadministratoren können nach Bedarf Berechtigungen für Schlüssel erteilen (und widerrufen).

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls 

Installieren des npm-Moduls für Azure Key Vault

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel wird ein neuer Key Vault-Dienst in Azure erstellt:

```javascript
const msRestAzure = require('ms-rest-azure');
const KeyVaultManagementClient = require('azure-arm-keyvault');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const vaultName = 'your-new-vault';
const tenantGUID = 'your-tenant-guid';

// Interactive Login
let client;
msRestAzure
  .interactiveLogin()
  .then(credentials => {
    client = new KeyVaultManagementClient(credentials, subscriptionId);
    return client.vaults.list();
  })
  .then(vaults => {
    console.dir(vaults, { depth: null, colors: true });
    const parameters = {
      location: 'East US',
      properties: {
        sku: { family: 'A', name: 'standard' },
        accessPolicies: [],
        enabledForDeployment: false,
        tenantId: tenantGUID
      }
    };
    console.info('Creating vault ${vaultName} ...');
    return client.vaults.createOrUpdate(resourceGroup, vaultName, parameters);
  })
  .then(vault => console.dir(vault, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error occured');
    console.dir(err, { depth: null, colors: true });
    return err;
  });
```

## <a name="samples"></a>Beispiele

- [Erste Schritte mit Key Vault in Node.js](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [Manage Azure resources and resource groups with Node.js (Verwalten von Azure-Ressourcen und -Ressourcengruppen mit Node.js)](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [Integrieren von Azure AD in eine NodeJS-Webanwendung](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
