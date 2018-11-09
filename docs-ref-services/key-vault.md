---
title: Azure Key Vault-Module für Node.js
description: Referenz zu Azure Key Vault-Modulen für Node.js
author: barclayn
ms.author: barclayn
manager: mbaldwin
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Key Vault
ms.openlocfilehash: 36bc5e97a5eea6e821f66bff9b3e8f610baa2dd0
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "51121849"
---
# <a name="azure-key-vault-modules-for-nodejs"></a><span data-ttu-id="32f33-103">Azure Key Vault-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="32f33-103">Azure Key Vault modules for Node.js</span></span>

<span data-ttu-id="32f33-104">Azure Key Vault unterstützt Sie dabei, kryptografische Schlüssel und Geheimnisse zu schützen, die von Cloudanwendungen und -diensten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="32f33-104">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span> <span data-ttu-id="32f33-105">Durch Verwenden von Key Vault können Sie Schlüssel und Geheimnisse (beispielsweise Authentifizierungsschlüssel, Schlüssel für Speicherkonten, Datenverschlüsselungsschlüssel, PFX-Dateien und Kennwörter) verschlüsseln, indem Sie Schlüssel verwenden, die durch Hardwaresicherheitsmodule (HSMs) geschützt werden.</span><span class="sxs-lookup"><span data-stu-id="32f33-105">By using Key Vault, you can encrypt keys and secrets (such as authentication keys, storage account keys, data encryption keys, .PFX files, and passwords) by using keys that are protected by hardware security modules (HSMs).</span></span> <span data-ttu-id="32f33-106">Zur Steigerung der Sicherheit können Sie Schlüssel in HSMs importieren oder in diesen generieren.</span><span class="sxs-lookup"><span data-stu-id="32f33-106">For added assurance, you can import or generate keys in HSMs.</span></span> <span data-ttu-id="32f33-107">Bei Verwendung dieser Option verarbeitet Microsoft Ihre Schlüssel in mit FIPS 140-2 (Level 2) überprüften HSMs (Hardware und Firmware).</span><span class="sxs-lookup"><span data-stu-id="32f33-107">If you choose to do this, Microsoft processes your keys in FIPS 140-2 Level 2 validated HSMs (hardware and firmware).</span></span>

<span data-ttu-id="32f33-108">Der Schlüsseltresor optimiert die Schlüsselverwaltung und ermöglicht es Ihnen, die Kontrolle über Schlüssel zu behalten, die für den Datenzugriff und die Verschlüsselung Ihrer Daten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="32f33-108">Key Vault streamlines the key management process and enables you to maintain control of keys that access and encrypt your data.</span></span> <span data-ttu-id="32f33-109">Entwickler können Schlüssel für Tests und Entwicklung innerhalb von Minuten erstellen und diese später nahtlos in Schlüssel für die Produktion migrieren.</span><span class="sxs-lookup"><span data-stu-id="32f33-109">Developers can create keys for development and testing in minutes, and then seamlessly migrate them to production keys.</span></span> <span data-ttu-id="32f33-110">Sicherheitsadministratoren können nach Bedarf Berechtigungen für Schlüssel erteilen (und widerrufen).</span><span class="sxs-lookup"><span data-stu-id="32f33-110">Security administrators can grant (and revoke) permission to keys, as needed.</span></span>

## <a name="management-package"></a><span data-ttu-id="32f33-111">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="32f33-111">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="32f33-112">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="32f33-112">Install the npm module</span></span> 

<span data-ttu-id="32f33-113">Installieren des npm-Moduls für Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="32f33-113">Install the Azure Key Vault npm module</span></span>

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a><span data-ttu-id="32f33-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="32f33-114">Example</span></span>

<span data-ttu-id="32f33-115">Mit diesem Beispiel wird ein neuer Key Vault-Dienst in Azure erstellt:</span><span class="sxs-lookup"><span data-stu-id="32f33-115">This example creates a new Key Vault service in Azure.</span></span>

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

## <a name="samples"></a><span data-ttu-id="32f33-116">Beispiele</span><span class="sxs-lookup"><span data-stu-id="32f33-116">Samples</span></span>

- [<span data-ttu-id="32f33-117">Erste Schritte mit Key Vault in Node.js</span><span class="sxs-lookup"><span data-stu-id="32f33-117">Getting started with Key Vault in Node.js</span></span>](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [<span data-ttu-id="32f33-118">Manage Azure resources and resource groups with Node.js (Verwalten von Azure-Ressourcen und -Ressourcengruppen mit Node.js)</span><span class="sxs-lookup"><span data-stu-id="32f33-118">Manage Azure resources and resource groups with Node.js</span></span>](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [<span data-ttu-id="32f33-119">Integrieren von Azure AD in eine NodeJS-Webanwendung</span><span class="sxs-lookup"><span data-stu-id="32f33-119">Integrating Azure AD into a NodeJS web application</span></span>](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

<span data-ttu-id="32f33-120">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="32f33-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
