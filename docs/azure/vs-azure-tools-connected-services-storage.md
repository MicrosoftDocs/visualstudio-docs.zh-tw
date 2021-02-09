---
title: 使用已連線的服務新增 Azure 儲存體 | Microsoft Docs
description: 使用 Visual Studio 將 Azure 儲存體服務相依性新增至您的應用程式已連線的服務
author: ghogen
manager: jmartens
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 08/13/2020
ms.author: ghogen
ms.openlocfilehash: a2aa5a0453b6a05c261d3cac853ab8265fb4e453
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844342"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>使用 Visual Studio 的已連接服務加入 Azure 儲存體

使用 Visual Studio，您可以使用 **已連線的服務** 功能，將下列任何一項連接到 Azure 儲存體：

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

## <a name="connect-to-azure-storage-using-connected-services"></a>使用已連線的服務連接到 Azure 儲存體

::: moniker range="vs-2017"

1. 在 Visual Studio 中，開啟您的專案。

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **已連線的服務** ] 節點，然後從內容功能表中選取 [ **加入已連接服務**]。

    ![新增 Azure 已連接服務](./media/vs-azure-tools-connected-services-storage/add-connected-service.png)

1. 在 [已連接服務] 頁面中，選取 [使用 Azure 儲存體的雲端儲存體]。

    ![新增 Azure 儲存體](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. 在 [Azure 儲存體] 對話方塊中，選取現有的儲存體帳戶，然後選取 [新增]。

    如果您需要建立儲存體帳戶，請移至下一個步驟。 否則，請前往步驟 6。

    ![將現有的儲存體帳戶新增到專案](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. 建立儲存體帳戶：

   1. 選取對話方塊底部的 [建立新的儲存體帳戶]。

   1. 填寫 [建立儲存體帳戶] 對話方塊，然後選取 [建立]。

       ![新的 Azure 儲存體帳戶](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. 顯示 [Azure 儲存體] 對話方塊時，新的儲存體帳戶會出現在清單中。 選取清單中的新儲存體帳戶，然後選取 [新增]。

1. 儲存體已連接服務會出現在您專案的 [服務參考] 節點之下。
:::moniker-end

:::moniker range=">=vs-2019"

1. 在 Visual Studio 中，開啟您的專案。

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **已連線的服務** ] 節點，然後從內容功能表中選取 [ **加入已連接服務**]。

    ![新增 Azure 已連接服務](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. 在 [ **已連線的服務** ] 索引標籤中，選取 [服務相依性的 + **]** 圖示。

    ![新增服務相依性](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. 在 [ **新增** 相依性] 頁面中，選取 [ **Azure 儲存體**]。

    ![新增 Azure 儲存體](./media/vs-azure-tools-connected-services-storage/vs-2019/add-azure-storage.png)

    如果您尚未登入，請登入您的 Azure 帳戶。 如果您沒有 Azure 帳戶，您可以註冊 [免費試用版](https://azure.microsoft.com/account/free)。

1. 在 [ **設定 Azure 儲存體** ] 畫面中，選取現有的儲存體帳戶，然後選取 **[下一步]**。

    如果您需要建立儲存體帳戶，請移至下一個步驟。 否則，請前往步驟 6。

    ![將現有的儲存體帳戶新增到專案](./media/vs-azure-tools-connected-services-storage/vs-2019/select-azure-storage-account.png)

1. 建立儲存體帳戶：

   1. 選取對話方塊底部的 [ **建立儲存體帳戶** ]。

   1. 填寫 **Azure 儲存體： [建立新** 的] 對話方塊，然後選取 [ **建立**]。

       ![新的 Azure 儲存體帳戶](./media/vs-azure-tools-connected-services-storage/vs-2019/create-storage-account.png)

   1. 顯示 [Azure 儲存體] 對話方塊時，新的儲存體帳戶會出現在清單中。 在清單中選取新的儲存體帳戶，然後選取 [ **下一步]**。

1. 輸入連接字串名稱，然後選擇您要將連接字串儲存在本機秘密檔案或 [Azure Key Vault](/azure/key-vault)中。

   ![指定連接字串](./media/vs-azure-tools-connected-services-storage/vs-2019/connection-string.png)

1. 當您完成此程式時，[ **變更的摘要** ] 畫面會顯示對您的專案所做的所有修改。 如果變更看起來沒問題，請選擇 [ **完成**]。

   ![變更摘要](./media/vs-azure-tools-connected-services-storage/vs-2019/summary-of-changes.png)

1. 儲存體已連接服務會出現在您專案的 [服務參考] 節點之下。
:::moniker-end

## <a name="see-also"></a>另請參閱

- [Azure 儲存體論壇](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Azure 儲存體文件](/azure/storage/)
- [已連線的服務 (Visual Studio for Mac)](/visualstudio/mac/connected-services)
