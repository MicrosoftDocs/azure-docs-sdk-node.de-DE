---
title: Erstellen eines Azure-Dienstprinzipals mit Node.js
description: Erfahren Sie, wie Sie die Dienstprinzipalauthentifizierung über Node.js verwenden.
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 98d52e21332138512d40ff2de9f5d3388fa596e4
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "51099019"
---
# <a name="create-an-azure-service-principal-with-nodejs"></a><span data-ttu-id="b1ff7-103">Erstellen eines Azure-Dienstprinzipals mit Node.js</span><span class="sxs-lookup"><span data-stu-id="b1ff7-103">Create an Azure service principal with Node.js</span></span> 

<span data-ttu-id="b1ff7-104">Wenn eine App Zugriff auf Ressourcen benötigt, können Sie eine Identität für die App einrichten und sie mit ihren eigenen Anmeldeinformationen authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-104">When an app needs to access resources, you can set up an identity for the app and authenticate the app with its own credentials.</span></span> <span data-ttu-id="b1ff7-105">Diese Identität wird als *Dienstprinzipal* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-105">This identity is known as a *service principal*.</span></span> <span data-ttu-id="b1ff7-106">Im Grunde erstellen Sie für Ihr Azure Active Directory-Konto Schlüssel, die Sie an das SDK übergeben, um eine Authentifizierung ohne Benutzereingriff oder die Eingabe von Benutzer/Kennwort zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-106">Essentially, you create keys for your Azure Active Directory account that you provide to the SDK to authenticate rather than requiring user intervention or username/password.</span></span>

<span data-ttu-id="b1ff7-107">Der Dienstprinzipal ermöglicht Folgendes:</span><span class="sxs-lookup"><span data-stu-id="b1ff7-107">The service principal approach enables you to:</span></span>
- <span data-ttu-id="b1ff7-108">Sie können der App-Identität Berechtigungen zuweisen, die sich von Ihren eigenen Berechtigungen unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-108">Assign permissions to the app identity that are different than your own permissions.</span></span> <span data-ttu-id="b1ff7-109">In der Regel sind diese Berechtigungen genau auf die Aufgaben der App beschränkt.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-109">Typically, these permissions are restricted to exactly what the app needs to do.</span></span>
- <span data-ttu-id="b1ff7-110">Sie können ein Zertifikat für die Authentifizierung beim Ausführen eines unbeaufsichtigten Skripts verwenden.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-110">Use a certificate for authentication when running an unattended script.</span></span>

<span data-ttu-id="b1ff7-111">In diesem Thema werden drei Methoden zum Erstellen eines Dienstprinzipals erläutert.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-111">This topic shows you three techniques for creating a service principal.</span></span>

- <span data-ttu-id="b1ff7-112">Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="b1ff7-112">Azure portal</span></span>
- <span data-ttu-id="b1ff7-113">Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="b1ff7-113">Azure CLI 2.0</span></span>
- <span data-ttu-id="b1ff7-114">Azure SDK für Node.js</span><span class="sxs-lookup"><span data-stu-id="b1ff7-114">Azure SDK for Node.js</span></span>

## <a name="create-a-service-principal-using-the-azure-portal"></a><span data-ttu-id="b1ff7-115">Erstellen eines Dienstprinzipals mit dem Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="b1ff7-115">Create a service principal using the Azure portal</span></span>

<span data-ttu-id="b1ff7-116">Führen Sie die im Thema [Erstellen einer Azure Active Directory-Anwendung und eines Dienstprinzipals mit Ressourcenzugriff mithilfe des Portals](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/) beschriebenen Schritte aus, um den Dienstprinzipal zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-116">Follow the steps outlined in the topic, [Use portal to create an Azure Active Directory application and service principal that can access resources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/), to generate the service principal.</span></span>

## <a name="create-a-service-principal-using-the-azure-cli-20"></a><span data-ttu-id="b1ff7-117">Erstellen eines Dienstprinzipals mit der Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="b1ff7-117">Create a service principal using the Azure CLI 2.0</span></span>

<span data-ttu-id="b1ff7-118">Bei der Erstellung eines Dienstprinzipals mithilfe der [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) werden die folgenden Schritte ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="b1ff7-118">Creating a service principal using the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) can be accomplished with the following steps:</span></span>

1. <span data-ttu-id="b1ff7-119">Laden Sie die [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) herunter.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-119">Download the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

2. <span data-ttu-id="b1ff7-120">Öffnen Sie ein Terminalfenster.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-120">Open a terminal window.</span></span>

3. <span data-ttu-id="b1ff7-121">Geben Sie den folgenden Befehl ein, um den Anmeldeprozess zu starten:</span><span class="sxs-lookup"><span data-stu-id="b1ff7-121">Type the following command to start the login process:</span></span>

    ```shell
    $ az login
    ```

4. <span data-ttu-id="b1ff7-122">Durch den Aufruf von `az login` werden eine URL und ein Code zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-122">Calling `az login` results in a URL and a code.</span></span> <span data-ttu-id="b1ff7-123">Navigieren Sie zur angegebenen URL, geben Sie den Code ein, und melden Sie sich mit Ihrer Azure-Identität an. (Dies geschieht unter Umständen automatisch, wenn Sie bereits angemeldet sind.)</span><span class="sxs-lookup"><span data-stu-id="b1ff7-123">Browse to the specified URL, enter the code, and login with your Azure identity (this may happen automatically if you're already logged in).</span></span> <span data-ttu-id="b1ff7-124">Sie können dann über die CLI auf Ihr Konto zugreifen.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-124">You'll then be able to access your account via the CLI.</span></span>

5. <span data-ttu-id="b1ff7-125">Rufen Sie Ihr Abonnement und die Mandanten-ID ab:</span><span class="sxs-lookup"><span data-stu-id="b1ff7-125">Get your subscription and tenant id:</span></span>

    ```shell
    $ az account list
    ```

    <span data-ttu-id="b1ff7-126">Nachfolgend sehen Sie ein Beispiel für die Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="b1ff7-126">The following shows an example of the output:</span></span>

    ```shell
    {
    "cloudName": "AzureCloud",
    "id": "<subscriptionId>",
    "isDefault": true,
    "name": "<subscriptionName>",
    "registeredProviders": [],
    "state": "Enabled",
    "tenantId": "<tenantId>",
        "user": {
            "name": "hello@example.com",
            "type": "user"
        }
    }
    ```

    <span data-ttu-id="b1ff7-127">**Notieren Sie die Abonnement-ID, da sie in Schritt 7 verwendet wird.**</span><span class="sxs-lookup"><span data-stu-id="b1ff7-127">**Note the subscription ID as it will be used in Step 7.**</span></span>

6. <span data-ttu-id="b1ff7-128">Erstellen Sie einen Dienstprinzipal, um ein JSON-Objekt mit den anderen Informationen abzurufen, die Sie für die Authentifizierung mit Azure benötigen.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-128">Create a service principal to get a JSON object containing the other pieces of information you need to authenticate with Azure.</span></span>

    ```shell
    $ az ad sp create-for-rbac
    ```

    <span data-ttu-id="b1ff7-129">Nachfolgend sehen Sie ein Beispiel für die Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="b1ff7-129">The following shows an example of the output:</span></span>

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    <span data-ttu-id="b1ff7-130">**Notieren Sie sich die Werte für Mandant, Name und Kennwort, da sie in Schritt 7 verwendet werden.**</span><span class="sxs-lookup"><span data-stu-id="b1ff7-130">**Note the tenant, name, and password values as they'll be used in Step 7.**</span></span>

7. <span data-ttu-id="b1ff7-131">Richten Sie die Umgebungsvariablen ein. Ersetzen Sie dabei die Platzhalter „&lt;subscriptionId>“, „&lt;tenant>“, „&lt;name>“ und „&lt;password>“ durch die in den Schritten 4 und 5 abgerufenen Werte.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-131">Set up the environment variables - replacing the &lt;subscriptionId>, &lt;tenant>, &lt;name>, and &lt;password> placeholders with the values you obtained in steps 4 and 5.</span></span> 

    <span data-ttu-id="b1ff7-132">**Verwenden von Bash**</span><span class="sxs-lookup"><span data-stu-id="b1ff7-132">**Using bash**</span></span>

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    <span data-ttu-id="b1ff7-133">**Mithilfe von PowerShell**</span><span class="sxs-lookup"><span data-stu-id="b1ff7-133">**Using PowerShell**</span></span>

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a><span data-ttu-id="b1ff7-134">Erstellen eines Dienstprinzipals mit dem Azure SDK für Node.js</span><span class="sxs-lookup"><span data-stu-id="b1ff7-134">Create a service principal using the Azure SDK for Node.js</span></span>

<span data-ttu-id="b1ff7-135">Verwenden Sie zum programmgesteuerten Erstellen eines Dienstprinzipals mit JavaScript das [ServicePrincipal-Skript](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span><span class="sxs-lookup"><span data-stu-id="b1ff7-135">To programmatically create a service principal using JavaScript, use the [ServicePrincipal script](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span></span>   

## <a name="using-the-service-principal"></a><span data-ttu-id="b1ff7-136">Verwenden des Dienstprinzipals</span><span class="sxs-lookup"><span data-stu-id="b1ff7-136">Using the service principal</span></span>

<span data-ttu-id="b1ff7-137">Nach der Erstellung des Dienstprinzipals veranschaulicht der folgende JavaScript-Codeausschnitt, wie Sie die Dienstprinzipalschlüssel für die Authentifizierung mit dem Azure SDK für Node.js verwenden.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-137">Once you have a service principal, the following JavaScript code snippet illustrates how to use the service principal keys to authenticate with the Azure SDK for Node.js.</span></span> <span data-ttu-id="b1ff7-138">Passen Sie die folgenden Platzhalter an: „&lt;clientId or appId>“, „&lt;secret or password>“ und „&lt;domain or tenant>“.</span><span class="sxs-lookup"><span data-stu-id="b1ff7-138">Modify the following placeholders: &lt;clientId or appId>, &lt;secret or password>, and &lt;domain or tenant>,</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithServicePrincipalSecret(
  <clientId or appId>,
  <secret or password>,
  <domain or tenant>,
  (err, credentials) => {
    if (err) throw err

    let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

    // ..use the client instance to manage service resources.
  }
);
```
