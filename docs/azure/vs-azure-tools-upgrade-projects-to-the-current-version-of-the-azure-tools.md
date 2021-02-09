---
title: 將專案升級到目前版本的 Azure Tools
description: 了解如何在 Visual Studio 中將 Azure 專案升級至目前版本的 Azure Tools
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: f9f806ad2d5e9d72d9459ba48c0d7c9525acb30e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99843770"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>如何將專案升級為目前版本的 Azure Tools for Visual Studio
## <a name="overview"></a>概觀
安裝目前版本的 Azure Tools (或是比 1.6 版更新的舊版) 之後，任何使用 1.6 版 (2011 年 11 月) 以前的 Azure Tools 所建立的專案，在您開啟時會立即自動升級。 如果您使用這些工具的 1.6 版 (2011 年 11 月) 建立專案，且仍然安裝該版本，您可以在較舊版本中開啟這些專案，稍後再決定是否要將它們升級。

## <a name="how-your-project-changes-when-you-upgrade-it"></a>專案升級時有何變更
如果專案自動升級，或您指定要將它升級，您的專案會修改為使用目前版本的某些組件，某些屬性也會變更，如本節所述。 如果您的專案需要其他變更，才能與較新版本的工具相容，您必須手動進行這些變更。

* Web 角色的 web.config 檔案和背景工作角色的 app.config 檔案會更新為參考較新版的 Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener.dll。
* Microsoft.WindowsAzure.StorageClient.dll、Microsoft.WindowsAzure.Diagnostics.dll 和 Microsoft.WindowsAzure.ServiceRuntime.dll 組件會升級至新的版本。
* 已儲存在 Azure 專案檔 (.ccproj) 的發佈設定檔，將會移到 **Publish** 子目錄中的另一個檔案，副檔名為 .azurePubXml。
* 發佈設定檔中的某些屬性會更新為支援新的和變更的功能。 **AllowUpgrade** 會取代為 **DeploymentReplacementMethod**，因為您可以同時更新或累加式更新已部署的雲端服務。
* **UseIISExpressByDefault** 屬性已加入並設定為 false，因此使用於偵錯的 Web 伺服器並不會自動從 Internet Information Services (IIS) 變更為 IIS Express。 IIS Express 是由較新版本的工具所建立之專案的預設 Web 伺服器。
* 如果 Azure 快取裝載於一或多個專案的角色，當專案升級時，服務組態 (.cscfg 檔) 和服務定義 (.csdef 檔) 中的某些屬性會變更。 如果專案使用 Azure 快取 NuGet 封裝，專案會升級到最新版的封裝。 您應該開啟 web.config 檔案，並確認用戶端組態在升級程序期間已妥善維護。 如果您加入 Azure 快取用戶端組件的參考，而未使用 NuGet 封裝，則不會更新這些組件。您必須手動更新對於新版本的參考。

> [!IMPORTANT]
> 在 F# 專案中，您必須手動更新 Azure 組件的參考，使它們參考這些組件的較新版本。
>
>

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>如何將 Azure 專案升級至目前版本
1. 將目前版本的 Azure tools 安裝到您想要用於升級專案的 Visual Studio 安裝，然後開啟您想要升級的專案。 如果專案是使用 1.6 版 (2011 年 11 月) 以前的 Azure Tools 建立，專案會自動升級至目前版本。 如果專案是使用 2011 年 11 月版本建立，且仍然安裝該版本，則會在該版本中開啟專案。
2. 在 [方案總管] 中，開啟專案節點的捷徑功能表，選擇 [屬性]，然後在出現的對話方塊中選擇 [應用程式] 索引標籤。

    [**應用程式**] 索引標籤會顯示與專案相關的工具版本。 如果出現目前版本的 Azure Tools，表示已經升級專案。 若您所安裝的工具版本比索引標籤顯示的版本還要新，則會出現 [**升級**] 按鈕。
3. 選擇 [**升級**] 按鈕，將專案升級為最新版的工具。
4. 建置專案，然後解決因為 API 變更而造成的任何錯誤。 如需如何針對新版本來修改程式碼的相關資訊，請參閱特定 API 的文件。
