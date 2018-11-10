---
title: 進行偵錯 Azure 雲端服務選項 |Microsoft Docs
description: 偵錯 Azure 雲端服務
author: mikejo5000
manager: douge
ms.assetid: 80755da7-8350-4f5c-97ce-2962beabb36d
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/18/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: bd2608371871b7adc925fc11927fe061b00a1ec6
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001973"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>了解針對 Azure 雲端服務進行偵錯的各種方式
本文章提供偵錯 Azure 雲端服務的各種方法連結。 

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>在 Visual Studio 中的 Azure 雲端服務進行偵錯
您可以節省時間和金錢，藉由使用 Azure 計算模擬器來偵錯雲端服務在本機電腦上。 您在部署之前，在本機偵錯服務，您可以改善可靠性和效能而不需支付運算時間。 不過，只有當您在 Azure 中執行雲端服務時，可能會發生一些錯誤。 只有當您在 Azure 中執行雲端服務時，才會發生的錯誤可以藉由啟用遠端偵錯時發行您的服務，並接著將偵錯工具附加至角色執行個體進行偵錯。 如需詳細資訊，請參閱 <<c0> [ 偵錯您本機電腦上的雲端服務](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer)。

## <a name="using-intellitrace"></a>使用 IntelliTrace 
如果您使用 Visual Studio Enterprise 來撰寫角色設為目標的.NET Framework 4.5，您可以啟用 IntelliTrace，您會部署 Azure 雲端服務從 Visual Studio 的時間。 IntelliTrace 提供您可以使用 Visual Studio 偵錯應用程式，如同它已在 Azure 中執行的記錄檔。 如需詳細資訊，請參閱 <<c0> [ 偵錯發佈的雲端服務使用 IntelliTrace 和 Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=623016)。

## <a name="remote-debugging"></a>遠端偵錯 
您可以啟用遠端偵錯您的雲端服務時，當您部署雲端服務，從 Visual Studio。 如果您選擇啟用遠端偵錯部署，執行每個角色執行個體的虛擬機器上安裝遠端偵錯服務。 這些服務-例如`msvsmon.exe`-不會影響效能或造成額外成本。 如需詳細資訊，請參閱 <<c0> [ 偵錯雲端服務在 Azure 中的](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure)。

## <a name="next-steps"></a>後續步驟
- [Azure 雲端服務或 VM，在 Visual Studio 中的偵錯](./vs-azure-tools-debug-cloud-services-virtual-machines.md)-了解如何偵錯 Azure 雲端服務的詳細資訊。