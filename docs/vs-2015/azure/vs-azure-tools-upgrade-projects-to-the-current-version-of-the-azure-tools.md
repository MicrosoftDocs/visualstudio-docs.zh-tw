---
title: 如何將專案升級至目前版本的 Azure tools |Microsoft Docs
description: 了解如何在 Visual Studio 中的將 Azure 專案升級至最新版的 Azure 工具
author: ghogen
manager: douge
assetId: 1d64070a-078d-468a-87f4-e6715de6475f
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: c5fb70f2dd09338dd2e2f6b01cb60bf2be0cdbdd
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001986"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>如何將專案升級到最新版本的 Azure Tools for Visual Studio
## <a name="overview"></a>總覽
安裝最新版的 Azure 工具 （或先前的版本比 1.6 版本更新） 之後，使用 Azure Tools 所建立的任何專案發行之前 1.6 當您開啟自動升級 (第 2011 年 11 月)。 如果您使用這些工具的 1.6 (第 2011 年 11 月) 版本建立的專案，您仍然必須安裝該版本，您可以在較舊版本中開啟這些專案，並稍後決定是否要將它們升級。

## <a name="how-your-project-changes-when-you-upgrade-it"></a>當您在升級時，您的專案如何變更
如果專案自動升級，或您指定您想要將它升級，您的專案已修改為使用目前版本的某些組件，而且某些屬性也會變更，如本節所述。 如果您的專案需要其他變更，才能與較新版本的工具相容，您必須手動進行這些變更。

* Web 角色的 web.config 檔案和背景工作角色的 app.config 檔案更新為參考較新版的 Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitoirTraceListener.dll。
* Microsoft.WindowsAzure.StorageClient.dll、 Microsoft.WindowsAzure.Diagnostics.dll 和 Microsoft.WindowsAzure.ServiceRuntime.dll 組件會升級到新的版本。
* 已儲存在 Azure 專案檔 (.ccproj) 的發行設定檔會在移至另一個檔案，副檔名為.azurePubXml**發佈**子目錄。
* 發行設定檔中的某些屬性會更新以支援新的和變更功能。 **AllowUpgrade**被**DeploymentReplacementMethod**因為您可以同時或以累加方式更新部署的雲端服務。
* 屬性**UseIISExpressByDefault**加入並設定為 false，使用於偵錯的 web 伺服器不會自動將從網際網路資訊服務 (IIS) 變更為 IIS Express。 IIS Express 是由較新版本的工具建立之專案的預設 web 伺服器。
* 如果 Azure 快取裝載於一或多個專案的角色，當專案升級時，會變更的服務組態 （.cscfg 檔） 與服務定義 （.csdef 檔） 中的某些屬性。 如果專案使用 Azure 快取 NuGet 封裝，專案會升級至最新版本的封裝。 您應該開啟 web.config 檔案，並確認用戶端設定的升級程序期間已妥善維護。 如果您加入 Azure 快取的用戶端組件的參考，而不需使用 NuGet 套件，不會更新這些組件;您必須手動更新這些參考到新的版本。

> [!IMPORTANT]
> 針對F#專案，使其參考這些組件的較新版本，您必須手動更新 Azure 組件的參考。
> 
> 

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>如何將 Azure 專案升級至目前版本
1. 將目前版本的 Azure tools 安裝到您想要用於升級的專案的 Visual Studio 安裝，然後開啟您想要升級的專案。 如果專案使用 Azure Tools 建立以前 1.6 (2011 年 11 月)，專案會自動升級為最新版本。 如果專案建立使用 2011 年 11 月版本和仍然安裝該版本，該版本的專案隨即開啟。
2. 在 方案總管 中，開啟專案節點的捷徑功能表，選擇 **屬性**，然後選擇**應用程式**出現的對話方塊索引標籤。
   
    **應用程式**索引標籤會顯示與專案相關聯的工具版本。 如果出現目前版本的 Azure 工具，已經升級專案。 如果您已經安裝比索引標籤顯示時，較新版本的工具**升級**按鈕隨即顯示。
3. 選擇**升級** 按鈕，將專案升級為目前版本的工具。
4. 建置專案，並再解決任何錯誤所產生的 API 變更。 如需如何修改您的程式碼，新的版本資訊，請參閱特定 API 的文件。

