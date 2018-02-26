---
title: "適合我的發行選項為何？ | Microsoft Docs"
ms.custom: 
ms.date: 03/09/2017
ms.reviewer: riande
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ASP.NET, web applications, deployment, publishing
ms.assetid: 3A13F685-531C-457D-A98E-631888011E4B
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 22c9aa56ab63d0c7c3b342e2c50cf81045580b54
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2018
---
# 適合我的發行選項為何？

在 Visual Studio 內，可以直接將 Web 應用程式發行到下列目標：

- [Azure App Service](#azure-app-service)
- [Azure 虛擬機器](#azure-virtual-machines)
- [檔案系統](#file-system)
- [自訂目標 (IIS、FTP 等)](#custom-targets)，包含所有任意 Web 伺服器。

在 [發行] 索引標籤上，您可以選取現有的發行設定檔、匯入現有的發行設定檔，或使用這裡所述的選項建立新的發行設定檔。

## Azure App Service Web Apps

[Azure App Service Web Apps](/azure/app-service/app-service-web-overview) (或稱為 Web Apps) 可協助開發人員快速建立各種可調整的 Web 應用程式和服務，而不需要維護基礎結構。

您可以透過為上層 App Service 選擇[定價層或方案](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)，來決定 Web 應用程式計算能力的強弱。 您可以讓多個 Web 應用程式 (及其他應用程式類型) 共用相同的 App Service，而不需變更定價層。 例如，您可以在相同的 App Service 上同時裝載開發、預備和實際執行 Web 應用程式。

App Service 會在 Azure 中裝載雲端的虛擬機器上執行，並自動管理這些虛擬機器。 App Service 中的每個 Web 應用程式都會獲指派唯一的 \*.azurewebsites.net URL；「免費」以外的所有定價層都允許為網站指派自訂網域名稱。

### 選擇 Azure App Service Web Apps 的時機

- 您想要部署可透過網際網路存取的 Web 應用程式。
- 您想要依據需求自動調整 Web 應用程式，而不需要重新部署。
- 您不想要維護伺服器基礎結構 (包括軟體更新)。
- 您不需要在裝載 Web 應用程式的伺服器上進行任何電腦層級自訂。

> 如果您想要在自己的資料中心或其他內部部署電腦中使用 Azure App Service，則做法是使用 [Azure Stack](https://azure.microsoft.com/overview/azure-stack/)。

如需發佈 ASP.NET Core 應用程式的詳細資訊，請參閱[使用 Visual Studio 將 ASP.NET Core Web 應用程式發行到 Azure App Service](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。

## Azure 虛擬機器

[Azure 虛擬機器 (VM)](https://azure.microsoft.com/documentation/services/virtual-machines/) 可讓您建立和管理雲端中任意數目的計算資源。 若負有 VM 上所有軟體和更新的責任，即可依 Web 應用程式要求視需要進行自訂。 您可以透過「遠端桌面」直接存取虛擬機器，每部機器都會依需要維持其獲指派的 IP 位址。

調整裝載於虛擬機器的 Web 應用程式涉及依需求啟動其他 VM，然後部署必要軟體。 這個額外控制層可讓您在全球各地區以不同的方式調整。 例如，如果您的應用程式服務各種地區辦公室的員工，則可以依據這些地區域中的員工數目來調整 VM，而這可能會降低成本。

如需其他資訊，請參閱 Azure App Service、Azure 虛擬機器以及其他 Azure 服務之間的[詳細比較](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/)，而您可以使用 Visual Studio 中的 [自訂] 選項將這些 Azure 服務用作部署目標。

### 選擇 Azure App 虛擬機器的時機

- 您想要部署可透過網際網路存取的 Web 應用程式，並完整控制所指派 IP 位址的存留期。
- 您需要在伺服器上進行電腦層級自訂，包括特定資料庫系統、特定網路組態、磁碟分割等這類額外軟體。
- 您想要具有調整 Web 應用程式的細部控制層。
- 您因任何其他原因而需要直接存取裝載應用程式的伺服器。

> 如果您想要在自己的資料中心或其他內部部署電腦中使用 Azure 虛擬機器，則做法是使用 [Azure Stack](https://azure.microsoft.com/overview/azure-stack/)。


## 檔案系統

部署至檔案系統，表示只需要將 Web 應用程式的檔案複製到您自己電腦上的特定資料夾。 這最常用於進行測試，或者，如果電腦也執行 Web 伺服器，則用來部署應用程式以供有限數目的人員使用。 如果在網路上共用目標資料夾，則部署至檔案系統之後，其他可能接著將它部署至特定伺服器的人員將可使用 Web 應用程式檔案。

任何正在執行 Web 伺服器的本機電腦都可以透過網際網路或內部網路使用應用程式，而這取決於其設定方式和其所連接的網路 (如果您將電腦直接連線至網際網路，請特別注意保護它免受外部安全性威脅)。因為您可以管理這些電腦，所以可以完全控制軟體和硬體組態。

請注意，如果您因任何原因 (例如電腦存取) 而無法使用 Azure App Service 或 Azure 虛擬機器這類雲端服務，則可以在自己的資料中心內使用 [Azure Stack](https://azure.microsoft.com/overview/azure-stack/)。 Azure Stack 既可讓您透過 Azure App Service 和「Azure 虛擬機器」來管理和使用計算資源，又可讓所有項目保留在內部部署環境中。

### 選擇檔案系統部署的時機

- 您只需要將應用程式部署至檔案共用，而其他人將從該檔案共用部署至不同伺服器。
- 您只需要本機測試部署。
- 您想要個別檢查並可能修改應用程式檔案，再將它們傳送至另一個部署目標。

如需部署 .NET Core 應用程式的詳細資訊，請參閱[使用 Visual Studio 部署 .NET Core 應用程式](/dotnet/core/deploying/deploy-with-vs)。

## 自訂目標

自訂目標可讓您將 Web 應用程式部署至 Azure App Service、Azure 虛擬機器或本機檔案系統以外的目標。 它可以部署至檔案系統或您具有存取權的任何其他伺服器 (網際網路或內部網路)，包括其他雲端服務上的伺服器。 它可以使用 Web 部署 (檔案或 .ZIP) 和 FTP。

選擇自訂目標時，Visual Studio 會提示您輸入設定檔名稱，接著收集其他**連線**資訊，包括目標伺服器或位置、網站名稱和認證。 您可以在 [設定] 索引標籤上控制下列行為：

- 您想要部署的組態。
- 是否要從目的地中移除現有的檔案。
- 是否要在發行時預先編譯。
- 是否要將 [App_Data] 資料夾中的檔案從部署中排除。

您可以在 Visual Studio 中建立任意數目的自訂部署設定檔，這可讓您利用不同的設定來管理設定檔。

### 選擇自訂部署的時機

- 您是在非 Azure 且可透過 URL 存取的提供者上使用雲端服務。
- 您想要使用認證進行部署，但這些認證不是您在 Visual Studio 內使用的認證或直接繫結至 Azure 帳戶的認證。
- 您想要在每次部署時刪除目標中的檔案。

如需發佈到 IIS 的詳細資訊，請參閱[使用 ASP.NET 3.5 和 ASP.NET 4.5 的 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) 和[在執行 IIS 的遠端電腦上對 ASP.NET 進行遠端偵錯](../../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。