---
title: 已連線的服務
description: 瞭解如何從 Visual Studio for Mac 內將 Azure 資料儲存體、驗證及推播通知新增至跨平臺應用程式。
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: sayedihashimi
ms.author: sayedha
ms.date: 11/06/2018
ms.topic: how-to
ms.openlocfilehash: 69ad6007283b3c56a8d0e5902cc2b9bdc445f220
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847081"
---
# <a name="connected-services-walkthrough"></a>已連線的服務逐步解說

「已連線的服務」工作流程可將 Azure 入口網站工作流程帶入 Visual Studio for Mac 中，讓您不必離開專案，就能新增服務。

本逐步解說將示範如何新增 Azure 後端服務，以將雲端資料儲存體、驗證及推播通知新增至跨平台 Xamarin.Forms 可攜式類別庫 (PCL) 應用程式。

1. 從按兩下方案中的 [已連線的服務] 節點開始著手，這會顯示 [服務資源庫]。
  這是一份應用程式類型可用的所有服務清單。 按一下某個服務 (例如 [採用 Azure App Service 的行動後端]) 來選取該服務。

    [![Visual Studio for Mac 中的已連線的服務節點](media/connected-services-image001-sml.png "Visual Studio for Mac 中的已連線的服務節點")](media/connected-services-image001.png#lightbox)

2. [服務詳細資料] 頁面會有該服務的描述，以及要安裝的相依性。
  按一下 [新增] 按鈕以將相依性新增至應用程式：

    [![使用 Azure 的行動後端](media/connected-services-image002-sml.png "使用 Azure 的行動後端")](media/connected-services-image002.png#lightbox)

3. 必須將相依性新增至 PCL 和平台專屬專案，才能運作。
  選取核取方塊以將服務新增至每個將參考它 (直接或間接) 的專案：

    [![檢查所有應該參考服務的專案](media/connected-services-image003-sml.png "檢查所有應該參考服務的專案")](media/connected-services-image003.png#lightbox)

4. 在 NuGet 的 [接受授權] 對話方塊上，選擇 [接受]。
  可能有兩個要接受的對話方塊，一個用於 MobileClient 和相依性，另一個用於離線資料同步處理所需的 SQLiteStore：

    [![接受授權合約](media/connected-services-image004-sml.png "接受授權合約")](media/connected-services-image004.png#lightbox)

    ![接受授權視窗](media/connected-services-image005.png "接受授權視窗")

5. 新增相依性之後，系統會要求您使用要用來與 Azure 通訊的帳戶進行登入。
  如果您已經使用 Microsoft ID 登入，Visual Studio for Mac 將會嘗試擷取您的 Azure 訂用帳戶及與其相關的任何應用程式服務。 如果您沒有任何訂用帳戶，則可以在 Azure 入口網站中註冊免費試用或購買訂用帳戶方案，來新增一個訂用帳戶。

6. 從清單中選取一個應用程式服務。 這會在 `MobileServiceClient` 物件的範本程式碼中填入 Azure 上對應的應用程式服務 URL：

    [![從清單中選取 app service](media/connected-services-image006-sml.png "從清單中選取 app service")](media/connected-services-image006.png#lightbox)

    如果沒有列出任何服務，請按一下 [新增] 按鈕 (請參閱步驟 9)。

7. 將 `MobileServiceClient` 的範本程式碼複製到 PCL。 在只有一個檔案執行個體的情況下，檔案位置不重要。
  建議的方法是建立一個 `AzureService` 類別來處理所有 Azure 互動和使用 `MobileServiceClient`：

    ![將設定程式碼複製到 ap](media/connected-services-image007.png "將設定程式碼複製到應用程式")

8. 依照 **後續步驟** 中文件的指示，將資料、離線同步處理、驗證及推播通知新增至應用程式：

    [![請參閱後續步驟指示](media/connected-services-image008-sml.png "請參閱後續步驟指示")](media/connected-services-image008.png#lightbox)

9. 如果您沒有任何現有的應用程式服務，則可以從 Visual Studio for Mac 內建立新的服務。
  按一下服務清單左下角的 [新增] 按鈕，以開啟 [新增 App Service] 對話方塊：

    [![在 Visual Studio for Mac 中建立新的 app service](media/connected-services-image009-sml.png "在 Visual Studio for Mac 中建立新的 app service")](media/connected-services-image009.png#lightbox)

新服務會需要下列參數：

- **App Service 名稱** – 方案的唯一名稱/識別碼
- **訂用帳戶** – 您要用來支付服務費用的訂用帳戶
- **資源群組** – 一種組織專案所有 Azure 資源的方式。 請選擇使用現有的或是建立一個新的。 如果這是您的第一個 Azure 服務，請建立一個新的。
- **服務方案** – 針對使用服務的任何資源，決定其位置與費用。 請選擇使用現有的或是建立一個新的。 如果這是您的第一個 Azure 服務，請使用預設值或在免費層 (F1) 中建立一個新的。

如需詳細資訊，請瀏覽 [Mobile Apps 文件](/azure/app-service-mobile/)。

## <a name="see-also"></a>請參閱

- [已連線的服務 (Windows 上的 Visual Studio)](/visualstudio/azure/vs-azure-tools-connected-services-storage)