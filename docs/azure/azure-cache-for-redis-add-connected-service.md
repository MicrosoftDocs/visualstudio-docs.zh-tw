---
title: 使用已連線的服務來新增 Azure Cache for Redis |Microsoft Docs
description: 使用 Visual Studio 加入已連線的服務，將 Azure Cache for Redis 支援新增至您的應用程式
author: AngelosP
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: dd08cc9cc44b0866d718fe03392e99d5fa6467b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841167"
---
# <a name="add-azure-cache-for-redis-by-using-visual-studio-connected-services"></a>使用 Visual Studio 來新增 Azure Cache for Redis 已連線的服務

使用 Visual Studio，您可以使用 **已連線的服務** 功能，將下列任何一項連接到 Azure Cache for Redis：

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

## <a name="connect-to-azure-cache-for-redis-using-connected-services"></a>使用已連線的服務連接到 Azure Cache for Redis

1. 在 Visual Studio 中，開啟您的專案。

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **已連線的服務** ] 節點，然後從內容功能表中選取 [ **加入已連接服務**]。

1. 在 [ **已連線的服務** ] 索引標籤中，選取 [服務相依性的 + **]** 圖示。

    ![新增服務相依性](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. 在 [ **新增** 相依性] 頁面中，選取 [ **Azure Cache for Redis**]。

    ![新增 Azure Cache for Redis](./media/azure-redis-cache-add-connected-service/azure-redis-cache.png)

    如果您尚未登入，請登入您的 Azure 帳戶。 如果您沒有 Azure 帳戶，您可以註冊 [免費試用版](https://azure.microsoft.com/account/free)。

1. 在 [ **設定 Azure Cache for Redis** ] 畫面中，選取現有的 Azure Cache for Redis，然後選取 **[下一步]**。

    如果您需要建立新的元件，請移至下一個步驟。 否則，請跳至步驟 7。

    ![連接至現有的 Azure Cache for Redis](./media/azure-redis-cache-add-connected-service/created-azure-redis-cache.png)

1. 若要建立 Azure Redis 快取：

   1. 選取畫面底部的 [ **建立新的 Azure Redis** 快取]。

   1. 填寫 **Azure Cache for Redis：建立新** 畫面，然後選取 [ **建立**]。

       ![新增 Azure Cache for Redis](./media/azure-redis-cache-add-connected-service/create-new-azure-redis-cache.png)

   1. 顯示 [ **設定 Azure Cache for Redis** ] 畫面時，新的快取會出現在清單中。 在清單中選取新的資料庫，然後選取 [ **下一步]**。

1. 輸入連接字串名稱，或選擇預設值，然後選擇您要將連接字串儲存在本機秘密檔案或 [Azure Key Vault](/azure/key-vault)中。

   ![指定連接字串](./media/azure-redis-cache-add-connected-service/connection-string.png)

1. 當您完成此程式時，[ **變更的摘要** ] 畫面會顯示對您的專案所做的所有修改。 如果變更看起來沒問題，請選擇 [ **完成**]。

   ![變更摘要](./media/azure-redis-cache-add-connected-service/summary-of-changes.png)

1. 連接會出現在 [**已連線的服務**] 索引標籤的 [**服務** 相依性] 區段下方。

   ![服務相依性](./media/azure-redis-cache-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>另請參閱

- [Azure Cache for Redis 產品頁面](https://azure.microsoft.com/services/cache)
- [Azure Cache for Redis 檔](/azure/azure-cache-for-redis/)
- [已連線的服務 (Visual Studio for Mac)](/visualstudio/mac/connected-services)