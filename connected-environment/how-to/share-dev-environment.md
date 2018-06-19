---
title: 如何共用開發環境 | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 3/12/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: douge
ms.openlocfilehash: 43d23caa039340345372076d02b3c4989cde5b01
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31883159"
---
# <a name="share-a-development-environment"></a>共用開發環境

使用已連線的環境，您可以與小組的其他成員共用您的開發環境。 每位開發人員都可以在自己的空間中工作，不用擔心中斷其他人的工作。 此外，在一個環境中一起工作可讓您以端對端方式測試程式碼，不必建立模型或模擬相依性。 如需詳細資訊，請參閱[了解小組開發](../get-started-nodejs-06.md)指南。

設定適用於多位開發人員的環境：
1. [在 Azure 中建立已連線的環境](../get-started.md)。 您必須具有所選 Azure 訂用帳戶的擁有者或參與者存取權。
1. 設定環境的**資源群組**以[授與參與者存取權](https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-configure)給每位小組成員。 您可以執行此命令來檢查環境的資源群組：`vsce env list`
1. 要求小組成員**選取環境**以在其中進行開發工作。
     * **命令列或 VS Code**：查看您可以存取的現有已連線的環境：`vsce env list`。 選取環境：`vsce env select`。
     * **Visual Studio IDE**：在 Visual Studio 中開啟專案，從 [啟動設定] 下拉式清單中選取 [Connected Environment for AKS] (適用於 AKS 之已連線的環境)。 在開啟的對話方塊中，選取現有的開發環境。

![Visual Studio [啟動設定] 下拉式清單](../images/LaunchSettings.png)