---
title: 使用已連線的服務新增 Azure 應用程式見解 |Microsoft Docs
description: 使用 Visual Studio 加入已連線的服務，為您的應用程式新增 Azure 應用程式見解
author: AngelosP
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 5b93d5b15cbbd3ffcb1f8afb65afe6e1c2c371b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841220"
---
# <a name="add-azure-application-insights-by-using-visual-studio-connected-services"></a>使用 Visual Studio 來新增 Azure 應用程式見解已連線的服務

使用 Visual Studio，您可以使用 **已連線的服務** 功能，將下列任何一項連線至 Azure 應用程式的見解：

- .NET Framework 主控台應用程式
- ASP.NET MVC ( .NET Framework)  
- ASP.NET Core
- .NET Core (包括主控台應用程式、WPF、Windows Forms、類別庫) 
- .NET Core 背景工作角色
- Azure Functions
- 通用 Windows 平臺應用程式
- Xamarin
- Cordova

已連接服務功能會將所有必要的參考和連接程式碼新增到您的專案中，並適當地修改組態檔。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 若是 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中已連線的服務](/visualstudio/mac/connected-services)。
## <a name="prerequisites"></a>必要條件

- 已安裝 Azure 工作負載的 Visual Studio。
- 其中一個支援類型的專案

## <a name="connect-to-azure-application-insights-using-connected-services"></a>使用已連線的服務連接到 Azure 應用程式見解

1. 在 Visual Studio 中，開啟您的專案。

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **已連線的服務** ] 節點，然後從內容功能表中選取 [ **加入已連接服務**]。

1. 在 [ **已連線的服務** ] 索引標籤中，選取 [服務相依性的 + **]** 圖示。

    ![新增服務相依性](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. 在 [ **新增** 相依性] 頁面中，選取 [ **Azure 應用程式見解**]。

    ![新增 Azure 應用程式見解](./media/azure-app-insights-add-connected-service/azure-app-insights.png)

    如果您尚未登入，請登入您的 Azure 帳戶。 如果您沒有 Azure 帳戶，您可以註冊 [免費試用版](https://azure.microsoft.com/account/free)。

1. 在 [ **設定 Azure 應用程式見解** ] 畫面中，選取現有的 Azure 應用程式 Insights 元件，然後選取 **[下一步]**。

    如果您需要建立新的元件，請移至下一個步驟。 否則，請跳至步驟 7。

    ![連接至現有的 Application Insights 元件](./media/azure-app-insights-add-connected-service/created-app-insights.png)

1. 若要建立 Application Insights 元件：

   1. 選取畫面底部的 [ **建立新的 Application Insights 元件** 。

   1. 填寫 **Application Insights：建立新** 畫面，然後選取 [ **建立**]。

       ![新的 Azure App 見解元件](./media/azure-app-insights-add-connected-service/create-new-app-insights.png)

   1. 顯示 [ **設定 Azure 應用程式見解** ] 畫面時，新的元件會出現在清單中。 選取清單中的新元件，然後選取 [ **下一步]**。

1. 輸入檢測金鑰名稱，或選擇預設值，然後選擇您要將連接字串儲存在本機秘密檔案或 [Azure Key Vault](/azure/key-vault)中。

   ![指定連接字串](./media/azure-app-insights-add-connected-service/connection-string.png)

1. 當您完成此程式時，[ **變更的摘要** ] 畫面會顯示對您的專案所做的所有修改。 如果變更看起來沒問題，請選擇 [ **完成**]。

   ![變更摘要](./media/azure-app-insights-add-connected-service/summary-of-changes.png)

1. 連接會出現在 [**已連線的服務**] 索引標籤的 [**服務** 相依性] 區段下方。

   ![服務相依性](./media/azure-app-insights-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>另請參閱

- [Azure 監視器產品頁面](https://azure.microsoft.com/services/monitor/)
- [Azure App Insights 檔](/azure/azure-monitor/app/app-insights-overview/)
- [已連線的服務 (Visual Studio for Mac)](/visualstudio/mac/connected-services)
