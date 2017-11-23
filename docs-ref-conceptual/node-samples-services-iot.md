---
title: Beispielcode zur Verwendung von Azure Messaging und IoT mit Node.js
description: Mit diesem Beispielcode wird die Verwendung von Azure Messaging und IoT mit Node.js veranschaulicht.
author: tomarcher
manager: douge
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: tarcher
ms.openlocfilehash: 5d7fc46edde0df844f8e4933bef672e619bd06fc
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="sample-code-for-using-azure-messaging-and-iot-with-nodejs"></a><span data-ttu-id="b4759-103">Beispielcode zur Verwendung von Azure Messaging und IoT mit Node.js</span><span class="sxs-lookup"><span data-stu-id="b4759-103">Sample code for using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="b4759-104">Mit dem folgenden Beispielcode wird die Verwendung von Azure Messaging und IoT mit Node.js veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="b4759-104">The following sample code illustrates using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="b4759-105">Wenn Sie Code für andere Aufgaben benötigen, können Sie die vollständige Liste mit den [Azure-Node.js-Beispielen](https://azure.microsoft.com/resources/samples/?term=nodejs) durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="b4759-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="b4759-106">**Azure IoT Hub**</span><span class="sxs-lookup"><span data-stu-id="b4759-106">**Azure IoT Hub**</span></span> ||
| [<span data-ttu-id="b4759-107">Azure IoT Hub – Ping</span><span class="sxs-lookup"><span data-stu-id="b4759-107">Azure IoT Hub ping</span></span>](https://github.com/Azure-Samples/iot-hub-node-ping) | <span data-ttu-id="b4759-108">Eine einfache Ping-Lösung zum Überprüfen der Gerätekonnektivität mit Azure IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="b4759-108">Simple ping solution to help validate a device connectivity to Azure IoT Hub.</span></span> |
| [<span data-ttu-id="b4759-109">Tweeten von Schwingungsanomalien, die von Azure IoT-Diensten für Daten von einem Intel Edison-System unter Node.js erkannt werden</span><span class="sxs-lookup"><span data-stu-id="b4759-109">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) | <span data-ttu-id="b4759-110">Ein IoT-Projekt mit Azure IoT Hub und Anzeige eines Geräteausführungsknotens zum Senden von Telemetriedaten und Analyse durch Azure IoT-Dienste.</span><span class="sxs-lookup"><span data-stu-id="b4759-110">IoT project using Azure IoT Hub and showing a device running node to send telemetry data and that is analyzed by Azure IoT services.</span></span> |
| <span data-ttu-id="b4759-111">**Intel Edison IoT**</span><span class="sxs-lookup"><span data-stu-id="b4759-111">**Intel Edison IoT**</span></span> ||
| <span data-ttu-id="b4759-112">[Get started with Intel Edison Azure IoT Starter Kit](https://github.com/Azure-Samples/iot-hub-node-intel-edison-getstartedkit) (Erste Schritte mit dem Azure IoT Intel Edison Starter Kit)</span><span class="sxs-lookup"><span data-stu-id="b4759-112">[Get started with Intel Edison Azure IoT Starter Kit](https://github.com/Azure-Samples/iot-hub-node-intel-edison-getstartedkit)</span></span> | <span data-ttu-id="b4759-113">Es wird gezeigt, wie Azure IoT mit dem Azure IoT Starter Kit für Intel Edison verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b4759-113">Demonstrates Azure IoT using the Azure IoT Starter Kit - Intel Edison.</span></span> |
| <span data-ttu-id="b4759-114">**MQTT**</span><span class="sxs-lookup"><span data-stu-id="b4759-114">**MQTT**</span></span> ||
| [<span data-ttu-id="b4759-115">MQTT- und HTTP-Gateway-Beispielmodule</span><span class="sxs-lookup"><span data-stu-id="b4759-115">Sample MQTT and HTTP Gateway modules</span></span>](https://github.com/Azure-Samples/iot-gateway-mqtt-http) | <span data-ttu-id="b4759-116">Enthält zwei Gatewaymodule, die MQTT- und HTTPS-Endpunkte im IoT Hub-Stil für den Upload von Telemetriedaten verfügbar machen (beim MQTT-Modul auch C2D-Messaging).</span><span class="sxs-lookup"><span data-stu-id="b4759-116">Provides two Gateway modules that expose IoTHub-style MQTT and HTTPS endpoints for telemetry upload, and in the case of MQTT module also C2D messaging.</span></span> |
| <span data-ttu-id="b4759-117">**Raspberry Pi**</span><span class="sxs-lookup"><span data-stu-id="b4759-117">**Raspberry Pi**</span></span> ||
| <span data-ttu-id="b4759-118">[Get Started with Microsoft Azure IoT Raspberry Pi Starter Kit](https://github.com/Azure-Samples/iot-hub-node-raspberrypi-getting-started) (Erste Schritte mit dem Microsoft Azure IoT Raspberry Pi Starter Kit)</span><span class="sxs-lookup"><span data-stu-id="b4759-118">[Get Started with Microsoft Azure IoT Raspberry Pi Starter Kit](https://github.com/Azure-Samples/iot-hub-node-raspberrypi-getting-started)</span></span> | <span data-ttu-id="b4759-119">Veranschaulicht die Verwendung des Azure IoT Raspberry Pi Starter Kit.</span><span class="sxs-lookup"><span data-stu-id="b4759-119">Illustrates using the Azure IoT Raspberry Pi Starter Kit.</span></span> |
| <span data-ttu-id="b4759-120">[Connect your Microsoft Azure IoT Raspberry Pi 3 Starter Kit to the remote monitoring solution](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/) (Verbinden Ihres Microsoft Azure IoT Raspberry Pi 3 Starter Kits mit der Remoteüberwachungslösung)</span><span class="sxs-lookup"><span data-stu-id="b4759-120">[Connect your Microsoft Azure IoT Raspberry Pi 3 Starter Kit to the remote monitoring solution](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)</span></span> | <span data-ttu-id="b4759-121">Es wird beschrieben, wie Sie für ein Raspberry Pi 3-Gerät eine Verbindung mit der Remoteüberwachungslösung der Azure IoT Suite herstellen.</span><span class="sxs-lookup"><span data-stu-id="b4759-121">Learn how to connect a Raspberry Pi 3 device to the Azure IoT Suite remote monitoring solution.</span></span> |
