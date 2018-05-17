---
title: Codebeispiele für Azure Messaging und IoT mit Node.js
description: Mit diesem Beispielcode wird die Verwendung von Azure-Messaging und IoT mit Node.js veranschaulicht.
author: rloutlaw
manager: routlaw
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: routlaw
ms.openlocfilehash: 3169c3ef0d204e902db47d81ba02b638a5eb02f5
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="sample-code-for-using-azure-messaging-and-iot-with-nodejs"></a><span data-ttu-id="dc7a5-103">Beispielcode zur Verwendung von Azure Messaging und IoT mit Node.js</span><span class="sxs-lookup"><span data-stu-id="dc7a5-103">Sample code for using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="dc7a5-104">Mit dem folgenden Beispielcode wird die Verwendung von Azure Messaging und IoT mit Node.js veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="dc7a5-104">The following sample code illustrates using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="dc7a5-105">Wenn Sie Code für andere Aufgaben benötigen, können Sie die vollständige Liste mit den [Azure-Node.js-Beispielen](https://azure.microsoft.com/resources/samples/?term=nodejs) durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="dc7a5-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="dc7a5-106">**Azure IoT Hub**</span><span class="sxs-lookup"><span data-stu-id="dc7a5-106">**Azure IoT Hub**</span></span> ||
| [<span data-ttu-id="dc7a5-107">Azure IoT Hub – Ping</span><span class="sxs-lookup"><span data-stu-id="dc7a5-107">Azure IoT Hub ping</span></span>](https://github.com/Azure-Samples/iot-hub-node-ping) | <span data-ttu-id="dc7a5-108">Eine einfache Ping-Lösung zum Überprüfen der Gerätekonnektivität mit Azure IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="dc7a5-108">Simple ping solution to help validate a device connectivity to Azure IoT Hub.</span></span> |
| [<span data-ttu-id="dc7a5-109">Tweeten von Schwingungsanomalien, die von Azure IoT-Diensten für Daten von einem Intel Edison-System unter Node.js erkannt werden</span><span class="sxs-lookup"><span data-stu-id="dc7a5-109">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) | <span data-ttu-id="dc7a5-110">Ein IoT-Projekt mit Azure IoT Hub und Anzeige eines Geräteausführungsknotens zum Senden von Telemetriedaten und Analyse durch Azure IoT-Dienste.</span><span class="sxs-lookup"><span data-stu-id="dc7a5-110">IoT project using Azure IoT Hub and showing a device running node to send telemetry data and that is analyzed by Azure IoT services.</span></span> |
| <span data-ttu-id="dc7a5-111">**Intel Edison IoT**</span><span class="sxs-lookup"><span data-stu-id="dc7a5-111">**Intel Edison IoT**</span></span> ||
| <span data-ttu-id="dc7a5-112">[Get started with Intel Edison Azure IoT Starter Kit](https://github.com/Azure-Samples/iot-hub-node-intel-edison-getstartedkit) (Erste Schritte mit dem Azure IoT Intel Edison Starter Kit)</span><span class="sxs-lookup"><span data-stu-id="dc7a5-112">[Get started with Intel Edison Azure IoT Starter Kit](https://github.com/Azure-Samples/iot-hub-node-intel-edison-getstartedkit)</span></span> | <span data-ttu-id="dc7a5-113">Es wird gezeigt, wie Azure IoT mit dem Azure IoT Starter Kit für Intel Edison verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="dc7a5-113">Demonstrates Azure IoT using the Azure IoT Starter Kit - Intel Edison.</span></span> |
| <span data-ttu-id="dc7a5-114">**MQTT**</span><span class="sxs-lookup"><span data-stu-id="dc7a5-114">**MQTT**</span></span> ||
| [<span data-ttu-id="dc7a5-115">MQTT- und HTTP-Gateway-Beispielmodule</span><span class="sxs-lookup"><span data-stu-id="dc7a5-115">Sample MQTT and HTTP Gateway modules</span></span>](https://github.com/Azure-Samples/iot-gateway-mqtt-http) | <span data-ttu-id="dc7a5-116">Enthält zwei Gatewaymodule, die MQTT- und HTTPS-Endpunkte im IoT Hub-Stil für den Upload von Telemetriedaten verfügbar machen (beim MQTT-Modul auch C2D-Messaging).</span><span class="sxs-lookup"><span data-stu-id="dc7a5-116">Provides two Gateway modules that expose IoTHub-style MQTT and HTTPS endpoints for telemetry upload, and in the case of MQTT module also C2D messaging.</span></span> |
| <span data-ttu-id="dc7a5-117">**Raspberry Pi**</span><span class="sxs-lookup"><span data-stu-id="dc7a5-117">**Raspberry Pi**</span></span> ||
| <span data-ttu-id="dc7a5-118">[Get Started with Microsoft Azure IoT Raspberry Pi Starter Kit](https://github.com/Azure-Samples/iot-hub-node-raspberrypi-getting-started) (Erste Schritte mit dem Microsoft Azure IoT Raspberry Pi Starter Kit)</span><span class="sxs-lookup"><span data-stu-id="dc7a5-118">[Get Started with Microsoft Azure IoT Raspberry Pi Starter Kit](https://github.com/Azure-Samples/iot-hub-node-raspberrypi-getting-started)</span></span> | <span data-ttu-id="dc7a5-119">Veranschaulicht die Verwendung des Azure IoT Raspberry Pi Starter Kit.</span><span class="sxs-lookup"><span data-stu-id="dc7a5-119">Illustrates using the Azure IoT Raspberry Pi Starter Kit.</span></span> |
| <span data-ttu-id="dc7a5-120">[Connect your Microsoft Azure IoT Raspberry Pi 3 Starter Kit to the remote monitoring solution](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/) (Verbinden Ihres Microsoft Azure IoT Raspberry Pi 3 Starter Kits mit der Remoteüberwachungslösung)</span><span class="sxs-lookup"><span data-stu-id="dc7a5-120">[Connect your Microsoft Azure IoT Raspberry Pi 3 Starter Kit to the remote monitoring solution](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)</span></span> | <span data-ttu-id="dc7a5-121">Es wird beschrieben, wie Sie für ein Raspberry Pi 3-Gerät eine Verbindung mit der Remoteüberwachungslösung der Azure IoT Suite herstellen.</span><span class="sxs-lookup"><span data-stu-id="dc7a5-121">Learn how to connect a Raspberry Pi 3 device to the Azure IoT Suite remote monitoring solution.</span></span> |
