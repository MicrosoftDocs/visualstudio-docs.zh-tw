---
title: Azure 服務的 Debug |Microsoft Docs
ms.date: 09/14/2018
ms.topic: how-to
helpviewer_keywords:
- debugger
ms.assetid: 3d434de3-ee5f-419d-9a94-ac4ac02d635b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 18635e4ecbbdb3c3c52be20b197c01168cdb12ff
ms.sourcegitcommit: dfbbf041e68ec3a4cd97196b19c9226a4793e702
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91878731"
---
# <a name="debug-azure-services-in-visual-studio"></a>在 Visual Studio 中將 Azure 服務進行 Debug 錯

您可以在不同的案例中使用 Visual Studio 來將 Azure 服務進行 debug 錯：

若要對裝載于的生產環境應用程式進行偵錯工具：

- 使用 Visual Studio Enterprise Azure App Service，請參閱 [使用快照偵錯工具來偵測即時 ASP.NET 應用程式](../debugger/debug-live-azure-applications.md)。

- Azure App Service 或 Service Fabric 使用 Application Insights，請參閱 [.net 應用程式例外狀況的偵錯工具快照](/azure/application-insights/app-insights-snapshot-debugger)。

- Azure 虛擬機器或 Azure 虛擬機器擴展集，請參閱 [使用快照偵錯工具來即時 ASP.NET azure 虛擬機器和 azure 虛擬機器擴展集](../debugger/debug-live-azure-virtual-machines.md)。

- Azure Kubernetes Service，請參閱 [使用快照偵錯工具進行即時 ASP.NET Azure Kubernetes Services 的](../debugger/debug-live-azure-kubernetes.md)偵測。

遠端偵錯：

- ASP.NET IIS (Azure App Service 或 Azure VM) 上的，請參閱 [azure 上的遠端偵錯程式 ASP.NET](remote-debugging-azure.md)。

- ASP.NET on Azure Service Fabric，請參閱 [Debug a remote Service Fabric 應用程式](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)

## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](../debugger/index.yml)
