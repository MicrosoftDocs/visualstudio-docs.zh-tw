---
title: 使用已連線的服務新增 Azure 應用程式設定 |Microsoft 檔
description: 使用 Visual Studio 已連線的服務，將 Azure 設定服務相依性新增至您的應用程式
author: ghogen
manager: ''
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 12/11/2020
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 250b89c983da039717982b31873a470172bde0f5
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683267"
---
# <a name="adding-azure-app-configuration-by-using-visual-studio-connected-services"></a>使用 Visual Studio 已連線的服務新增 Azure 應用程式設定

在本教學課程中，您將瞭解如何輕鬆地新增開始使用 Azure 應用程式設定來管理您在 Visual Studio 中 Web 專案的設定和功能旗標所需的一切。 藉由使用 Visual Studio 中的 [已連接服務] 功能，您可以讓 Visual Studio 自動新增您在 Azure 中連線到應用程式設定資源所需的所有程式碼、NuGet 套件和設定設定。 若要使用此功能，您必須使用 Visual Studio 2019 16.9 版或更新版本。

您可以使用 ASP.NET Core、.NET Core 主控台和 .NET Framework 專案中的應用程式設定已聯機服務功能。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 若是 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中已連線的服務](/visualstudio/mac/connected-services)。

## <a name="prerequisites"></a>必要條件

- 已安裝 Azure 工作負載的 Visual Studio。
- 其中一個支援類型的專案

## <a name="connect-to-azure-app-configuration-using-connected-services"></a>使用已連線的服務連接到 Azure 應用程式設定

1. 在 Visual Studio 中，開啟您的專案。

1. 在 [ **方案 Explorer**] 中，以滑鼠右鍵按一下 [ **已連結的服務** ] 節點，然後從內容功能表中選取 [ **加入已連接服務**]。

    ![新增 Azure 已連接服務](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. 在 [ **已連線的服務** ] 索引標籤中，選取 [服務相依性的 + **]** 圖示。

    ![新增服務相依性](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. 在 [ **新增** 相依性] 頁面中，選取 [ **Azure 應用程式** 設定]。

    ![新增應用程式設定](./media/vs-azure-tools-connected-services-app-configuration/add-azure-app-configuration.png)

    如果您尚未登入，請登入您的 Azure 帳戶。 如果您沒有 Azure 帳戶，您可以註冊 [免費試用版](https://azure.microsoft.com/free/dotnet)。

1. 在 [ **設定 Azure 應用程式設定** ] 畫面中，選取您的訂用帳戶和現有的設定存放區。 然後選取 [下一步]。

    如果您需要建立應用程式設定存放區，請移至下一個步驟。 否則，請前往步驟 6。

    ![將現有的設定帳戶新增至專案](./media/vs-azure-tools-connected-services-app-configuration/select-config-store.png)

1. 若要建立應用程式設定存放區：

   1. 選取 **應用程式** 設定存放區標頭右邊的 + 圖示。 

   1. 填寫 [ **Azure 應用程式設定：建立新** 的對話方塊]，然後選取 [ **建立**]。 請注意，資源名稱欄位必須是唯一的。 

       ![新的 Azure 應用程式設定存放區](./media/vs-azure-tools-connected-services-app-configuration/create-new-config-store.png)

   1. 顯示 [ **Azure 應用程式** 設定] 對話方塊時，新的設定存放區會出現在清單中。 選取這個新的存放區，然後選取 **[下一步]**。

1. 輸入連接字串名稱，然後選擇您要將連接字串儲存在本機秘密檔案或 [Azure 金鑰保存庫](/azure/key-vault)中。

   ![指定連接字串](./media/vs-azure-tools-connected-services-app-configuration/connection-string-app-config.png)

1. 當您完成此程式時，[ **變更的摘要** ] 畫面會顯示對您的專案所做的所有修改。 如果變更看起來沒問題，請選擇 [ **完成**]。

   ![變更摘要](./media/vs-azure-tools-connected-services-app-configuration/summary-of-changes-app-config.png)

1. 完成相依性設定 **程式之後，** Azure 應用程式設定現在會出現在專案的 [服務相依性 **]** 節點底下。

## <a name="next-steps"></a>下一步

瞭解 azure 應用程式設定 [檔](/azure/azure-app-configuration/overview)中的 Azure 應用程式設定。

## <a name="see-also"></a>另請參閱

- [在 App Configuration connected ASP.NET Core 應用程式中使用動態設定的教學課程](/azure/azure-app-configuration/enable-dynamic-configuration-aspnet-core)
- [已連線的服務 (Visual Studio for Mac)](/visualstudio/mac/connected-services)