---
title: 如何移轉並發佈 Azure 雲端服務的 Web 應用程式從 Visual Studio |Microsoft Docs
description: 了解如何移轉並發佈至 Azure 雲端服務 web 應用程式使用 Visual Studio
author: ghogen
manager: douge
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: c122b54a4e22285678d13213cc73d6492baba629
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002069"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>如何： 移轉並發佈 Azure 雲端服務的 Web 應用程式從 Visual Studio

若要充分利用的託管服務和 Azure 的調整能力，您可能想要移轉，並部署至 Azure 雲端服務 web 應用程式。 需要極少的變更。 本文章涵蓋部署到雲端服務針對 App Service，請參閱[部署 Azure App Service 中的 web 應用程式](/azure/app-service/app-service-deploy-local-git)。

> [!Important]
> 僅適用於特定的 ASP.NET、 Silverlight、 WCF 及 WCF 工作流程專案支援此移轉。 不支援 ASP.NET Core 專案。 請參閱[支援的專案範本](#supported-project-templates)。

## <a name="migrate-a-project-to-cloud-services"></a>將專案移轉至雲端服務

1. 以滑鼠右鍵按一下 web 應用程式專案，然後選取**轉換 > 轉換為 Microsoft Azure 雲端服務專案**。 （請注意，此命令不會顯示您已經有 web 角色專案方案中）。
1. Visual Studio 建立雲端服務專案中包含必要的 web 角色的方案。 此專案的名稱則會為您的應用程式專案，再加上後置詞是相同`.Azure`。
1. Visual Studio 也會設定**複製到本機**屬性設為 true 的 MVC 2、 MVC 3 中，MVC 4 和 Silverlight 商務應用程式所需的任何組件。 這個屬性會將這些組件加入至用於部署的服務封裝。

   > [!Important]
   > 如果您有其他的組件或檔案所需的這個 web 應用程式，您必須手動設定這些檔案的內容。 如需有關如何設定這些屬性的資訊，請參閱 <<c0> [ 的服務封裝中的 Include 檔](#include-files-in-the-service-package)。

### <a name="errors-and-warnings"></a>錯誤和警告

任何警告或發生的錯誤指出要部署至 Azure，例如遺漏的組件之前修正的問題。

如果您建置應用程式、 使用計算模擬器在本機執行，或將它發佈至 Azure，您可能會看到錯誤: 「 指定的路徑、 檔案名稱，或兩者都太長。 」 此錯誤表示完整的 Azure 專案名稱的長度超過 146 個字元。 若要修正此問題，請將方案移到不同的資料夾路徑較短。

如需如何將所有警告視為錯誤的詳細資訊，請參閱[使用 Visual Studio 設定 Azure 雲端服務專案](vs-azure-tools-configuring-an-azure-project.md)。

### <a name="test-the-migration-locally"></a>在本機測試移轉

1. 在 Visual Studio**方案總管**，以滑鼠右鍵按一下 新增的雲端服務專案，然後選取**設定為啟始專案**。
1. 選取 **偵錯 > 啟動偵錯**(F5) 來啟動 Azure 偵錯環境。 此環境特別提供模擬各種 Azure 服務。

### <a name="use-an-azure-sql-database-for-your-application"></a>Azure SQL Database 用於應用程式

如果您的 web 應用程式會使用內部部署 SQL Server 資料庫的連接字串，您必須改為將資料庫移轉至 Azure SQL Database，並更新連接字串。 如需進行此程序的指引，請參閱下列主題：

- [SQL Server 資料庫移轉至雲端中的 SQL Database](/azure/sql-database/sql-database-cloud-migrate)
- [使用.NET (C#) 與 Visual Studio 連線及查詢 Azure SQL database](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio)。

## <a name="publish-the-application-to-azure-cloud-service"></a>應用程式發行至 Azure 雲端服務

1. 建立必要的雲端服務和儲存體帳戶中 Azure 訂用帳戶上所述[準備發佈或部署 Azure 應用程式從 Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)。
1. 在 Visual Studio 中，以滑鼠右鍵按一下 應用程式專案，然後選取**發佈至 Microsoft Azure...** （此為不同於 發行 命令。）。
1. 在 **發佈 Azure 應用程式**，隨即出現，使用您的 Azure 訂用帳戶的帳戶登入，然後選取**下一步 >**。
1. 在 **設定 > 一般設定**索引標籤上，選取目標雲端服務**雲端服務**下拉式清單，以及您選擇的環境和組態。 
1. 在 [**設定 > 進階設定]**，選取儲存體帳戶，若要使用此項目，然後選取**下一步 >**。
1. 在 **診斷**，選擇是否要將資訊傳送至 Application Insights。
1. 選取 **下一步 >** 若要檢視摘要，然後選取**發佈**來開始進行部署。
1. Visual Studio 會開啟活動記錄視窗，您可以在此追蹤進度：

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. （選擇性）若要取消部署程序，以滑鼠右鍵按一下 活動記錄檔中的明細項目，然後選擇**取消並移除**。 此命令會停止部署程序，並從 Azure 刪除部署環境。 注意： 若要部署完成後，請移除此部署環境，您必須使用[Azure 入口網站](https://portal.azure.com)。
1. （選擇性）您的角色執行個體啟動後，Visual Studio 會自動顯示部署環境**伺服器總管 > 雲端服務**節點。 從這裡您可以檢視個別角色執行個體的狀態。
1. 若要存取您的應用程式部署之後，選擇 部署狀態時旁邊的箭號**已完成**會出現在**Azure 活動記錄檔**和 URL。 請參閱下表以了解如何從 Azure 啟動特定類型的 web 應用程式的詳細資料。

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>使用計算模擬器，並在 Azure 中啟動應用程式

可以連接到 Visual Studio 偵錯工具中，選取瀏覽器中啟動所有的應用程式類型**偵錯 > 啟動偵錯**(F5)。 ASP.NET 空白 Web 應用程式專案時，您必須先新增`.aspx`頁面中您的應用程式，並將它設定為您的 web 專案的 [開始] 頁面。

下表提供有關在 Azure 中啟動應用程式的詳細資料：

   | Web 應用程式類型 | 在 Azure 中執行 |
   | --- | --- | --- |
   | ASP.NET Web 應用程式<br/>（包括 MVC 2、 MVC 3、 MVC 4） | 選取中的 URL**部署**索引標籤**Azure 活動記錄檔**。 |
   | ASP.NET 空白 Web 應用程式 | 如果您有預設值`.aspx`在您的應用程式頁面上，選取中的 URL**部署**索引標籤**Azure 活動記錄檔**。 若要瀏覽至其他頁面，輸入下列格式的 URL 在瀏覽器： `<deployment_url>/<page_name>.aspx` |
   | Silverlight 應用程式<br/>Silverlight 商務應用程式<br/>Silverlight 導覽應用程式 | 瀏覽至您的應用程式使用下列 URL 格式的特定網頁： `<deployment_url>/<page_name>.aspx` |
    WCF 服務應用程式<br/>WCF 工作流程服務應用程式 | 設定`.svc`檔案 [開始] 頁面做為 WCF 服務專案。 然後瀏覽至 `<deployment_url>/<service_file>.svc` |
   | ASP.NET 動態實體<br/>ASP.NET Dynamic Data Linq to SQL | 下一節中所述，請更新連接字串。 然後瀏覽至`<deployment_url>/<page_name>.aspx`。 Linq to SQL，您必須使用 Azure SQL database。 |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>更新 ASP.NET 動態實體連接字串

1. (#Use-an-azuresql-database-for-your-application) 稍早所述，建立 ASP.NET 動態實體 web 應用程式的 SQL Azure 資料庫。
1. 加入資料表和欄位，您需要從 Azure 入口網站的這個資料庫。
1. 指定連接字串中的`web.config`以下列格式檔案，然後儲存檔案：

    ```xml
    <addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

    更新*connectionString*值與您的 SQL Azure 資料庫的 ADO.NET 連接字串，如下所示：

    ```xml
    XMLCopy<addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>支援的專案範本

可以移轉並發佈至雲端服務的應用程式必須使用其中一個範本下表中。 不支援 ASP.NET Core。

| 範本群組 | 專案範本 |
| --- | --- |
| Web | ASP.NET Web 應用程式 (.NET Framework) |
| Web | ASP.NET MVC 2 Web 應用程式 |
| Web | ASP.NET MVC 3 Web 應用程式 |
| Web | ASP.NET MVC4 Web 應用程式 |
| Web | ASP.NET 空白 Web 應用程式 （或站台） |
| Web | ASP.NET MVC 2 空白 Web 應用程式 |
| Web | ASP.NET Dynamic Data 實體 Web 應用程式 |
| Web | ASP.NET Dynamic Data Linq to SQL Web 應用程式 |
| Silverlight | Silverlight 應用程式 |
| Silverlight | Silverlight 商務應用程式 |
| Silverlight | Silverlight 導覽應用程式 |
| WCF | WCF 服務應用程式 |
| WCF | WCF 工作流程服務應用程式 |
| 工作流程 | WCF 工作流程服務應用程式 |

## <a name="next-steps"></a>後續步驟

- [準備發佈或部署 Azure 應用程式從 Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [設定具名驗證認證](vs-azure-tools-setting-up-named-authentication-credentials.md)。
