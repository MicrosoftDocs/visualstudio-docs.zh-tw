---
title: 步驟5：將您的 ASP.NET Core 應用程式部署至 Azure
description: 透過此影片和逐步指示，將您的 ASP.NET Core Web 應用程式部署至 Azure。
ms.custom: get-started
ms.date: 08/14/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: fc0729eccc6f1392561959dcdac0cf13dfc8e04a
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189754"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>步驟5：將您的 ASP.NET Core 應用程式部署至 Azure

請遵循這些步驟來將您的 ASP.NET Core 應用程式和其資料庫部署至 Azure。

_觀看此影片並跟著操作，以將您的第一個 ASP.NET Core 應用程式部署至 Azure。_

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>開啟您的專案

在 Visual Studio 2019 中開啟您的 ASP.NET Core 應用程式。 此應用程式應該已經設定 EF Core 並搭配使用 Web API，如同在[此教學課程的步驟 4](tutorial-aspnet-core-ef-step-04.md) 中所設定。

## <a name="publish-to-azure-app-service"></a>發佈至 Azure App Service

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [發行]。 在 [ **發佈** ] 嚮導中，選擇 [ **Azure** ] 作為目標。

   ![Azure App Service 1 的螢幕擷取畫面](media/vs-2019/app-service-screen-1.png)

1. 針對特定的目標，請選擇 **Azure App Service (Windows)**。

   ![Azure App Service 2 的螢幕擷取畫面](media/vs-2019/app-service-screen-2.png)

1. 選擇 [ **建立新的 Azure App Service**]。 如果您還沒有 Azure 帳戶，請按一下 [建立您的免費 Azure 帳戶] 並完成簡短的註冊程序。

   ![Azure App Service 3 的螢幕擷取畫面](media/vs-2019/app-service-screen-3.png)

1. 指定名稱和資源群組，或接受預設值，然後選擇 [ **建立**]。 資源群組只是在 Azure 中組織相關資源的一種方式，例如與儲存體帳戶、金鑰保存庫和資料庫搭配運作的服務。

   ![Azure App Service 4 的螢幕擷取畫面](media/vs-2019/app-service-screen-4.png)

1. 選擇 [完成]。 這些資源會在 Azure 中建立、部署應用程式，且 [ **發佈** ] 索引標籤會填入您剛才建立之內容的相關資訊。 [ **發行** ] 索引標籤可讓您使用相同的設定來發佈按鈕、顯示設定詳細資料，或讓您新增服務（例如資料庫）。

現在，新增 Azure SQL Server 資料庫。

1. 在 [ **發行** ] 索引標籤的 [ **服務** 相依性] 下的 [ **SQL Server 資料庫**] 旁，選擇 [ **設定**]。

1. 在下一個畫面上，選擇 [ **Azure SQL Database**]。

   ![Azure SQL Database 畫面的螢幕擷取畫面](media/vs-2019/app-service-azure-sql-db.png)

1. 在 [ **設定 SQL Database** ] 畫面上，選擇 [ **建立 SQL Database**。

   ![設定 SQL Database 畫面的螢幕擷取畫面](media/vs-2019/app-service-azure-sql-db-2.png)

1. 在 [ **Azure SQL Database：建立新** 的畫面] 上，建立新的資料庫伺服器。

   ![螢幕擷取畫面 Azure SQL Database：新建](media/vs-2019/app-service-azure-sql-db-3.png)

1. 在 [ **SQL Server：建立新** 的畫面上，選擇名稱、位置，然後指定系統管理員使用者名稱和密碼。

   ![Visual Studio 2019 建立 Azure SQL Server](media/vs-2019/app-service-azure-sql-db-overlayed.png)

## <a name="exploring-the-azure-portal-and-your-hosted-app"></a>探索 Azure 入口網站和您的託管應用程式

建立應用程式服務之後，您的網站會在瀏覽器中啟動。 當瀏覽器在載入時，您也可以在 Azure 入口網站中尋找該 App Service。 若您探索應用程式服務的可用選項，您會找到 [概觀] 區段，您可以在該處啟動和停止應用程式。

![Azure App Service 選項](media/vs-2019/vs2019-azure-app-service-menu-options.png)

### <a name="scalability"></a>延展性

您可以檢查選項，將應用程式相應增加及相應放大。相應增加是指將提供給裝載您應用程式的每個實例的資源。 相應放大是指增加裝載您應用程式之執行個體的數目。 您可以為應用程式設定自動調整，這樣系統會增加裝載您應用程式之執行個體的數量，以回應負載增加，然後會在負載減少時減少執行個體。

### <a name="security-and-compliance"></a>安全性與合規性

使用 Azure 來裝載應用程式的另一個好處是安全性和合規性。 Azure App Service 提供 ISO、SOC 和 PCI 合規性。 我們可以選擇使用 Azure Active Directory 或 Twitter、Facebook、Google 或 Microsoft 等社交登入來驗證使用者。 我們可以建立 IP 限制、管理服務身分識別、新增自訂網域、應用程式的 SSL 支援，以及透過應用程式的內容、設定和資料庫的可還原封存副本來設定備份。 這些功能可在 [驗證/授權]、[身分識別]、[備份] 和 [SSL 設定] 功能表選項中存取。

### <a name="deployment-slots"></a>部署位置

通常當您部署應用程式時，在應用程式重新啟動時會短暫停機。 藉由允許您部署至個別的準備執行個體或一組執行個體，並在將它們交換至生產環境之前先做好準備，部署位置得以避免此問題。 交換只是即時且順暢的流量重新導向。 交換之後，如果生產環境中有任何問題，您一律可以交換回到最近已知良好的生產狀態。

## <a name="update-connection-string"></a>更新連接字串

根據預設，Azure 預期新應用程式的連線使用名為 `DefaultConnection` 的連接字串連線至其新 SQL Server 資料庫。 我們在本教學課程系列中稍早前建立的應用程式，目前是使用名為 `AppDbContext` 的連接字串。 我們需要在 *appsettings.json* 和 *Startup.cs* 中變更此設定，然後重新部署應程式。

## <a name="test-the-app-running-in-azure"></a>測試應用程式在 Azure 中執行

瀏覽至 */Games* 路徑，您應該能夠新增遊戲並看到它被列出。 接下來，瀏覽至 */swagger* 路徑，您應該能夠從該處使用 Web API 端點，以確認應用程式的 API 能順利運作。

恭喜！ 您已經完成本教學課程系列影片！

## <a name="next-steps"></a>後續步驟

深入了解如何使用這些免費資源建構 ASP.NET Core 應用程式。

[ASP.NET Core 應用程式架構](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>另請參閱

- [使用 Visual Studio 將 ASP.NET Core 應用程式發行到 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2&preserve-view=true)