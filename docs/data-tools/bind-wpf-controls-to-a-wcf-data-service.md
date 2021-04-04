---
title: 將 WPF 控制項繫結至 WCF 資料服務
description: 將 WPF 控制項系結至 Visual Studio 中的 WCF 資料服務。 這些控制項會系結至封裝在 WCF 資料服務中的客戶記錄。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ae6a2fd6eac9f59a7836dae23d442962e1b2b27e
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215548"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>將 WPF 控制項繫結至 WCF 資料服務

您將在此逐步解說中，建立包含資料繫結控制項的 WPF 應用程式。 這些控制項會系結至封裝在 WCF 資料服務中的客戶記錄。 您也會加入按鈕，讓客戶可使用這些按鈕檢視及更新記錄。

本逐步解說將說明下列工作：

- 建立從 AdventureWorksLT 範例資料庫中的資料產生的實體資料模型。

- 建立將實體資料模型中的資料公開給 WPF 應用程式的 WCF 資料服務。

- 從 [資料來源] 視窗將項目拖曳至 WPF 設計工具，以建立一組資料繫結控制項。

- 建立可向前及向後巡覽客戶記錄的按鈕。

- 建立按鈕，將控制項中的資料變更儲存至 WCF 資料服務和基礎資料來源。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成這個逐步解說：

- Visual Studio

- 對執行中的 SQL Server 或 SQL Server Express (其中連結了 AdventureWorksLT 範例資料庫) 執行個體的存取權。 您可以從 [CodePlex 網站](https://archive.codeplex.com/?p=SqlServerSamples)下載 AdventureWorksLT 資料庫。

預先了解下列概念也有助於完成此逐步解說 (但非必要)：

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview)。

- [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]中的資料模型。

- 實體資料模型及 ADO.NET Entity Framework。 如需詳細資訊，請參閱 [Entity Framework 總覽](/dotnet/framework/data/adonet/ef/overview)。

- WPF 資料繫結。 如需詳細資訊，請參閱資料系結 [總覽](/dotnet/desktop-wpf/data/data-binding-overview)。

## <a name="create-the-service-project"></a>建立服務專案

1. 藉由建立 c # 或 Visual Basic **ASP.NET Web 應用程式** 專案來開始本逐步解說。 將專案命名為 **adventureworksservice.svc**。

2. 在 [方案總管] 中，以滑鼠右鍵按一下 **Default.aspx**，並選取 [刪除]。 本逐步解說不需要此檔案。

## <a name="create-an-entity-data-model-for-the-service"></a>建立服務的實體資料模型

若要使用 WCF 資料服務將資料公開給應用程式，您必須定義服務的資料模型。 WCF 資料服務支援兩種類型的資料模型：實體資料模型，以及使用 common language runtime 定義的自訂資料模型， (CLR) 執行介面的物件 <xref:System.Linq.IQueryable%601> 。 在此逐步解說中，您要建立資料模型的實體資料模型。

1. 在 [專案] 功能表上，按一下 [加入新項目]。

2. 在 [已安裝的範本] 清單中，按一下 [資料]，然後選取 [ADO.NET 實體資料模型] 專案項目。

3. 將 [名稱] 變更為 `AdventureWorksModel.edmx` ，然後按一下 [ **新增**]。

     [實體資料模型精靈] 隨即開啟。

4. 在 [選擇模型內容] 頁面中，按一下 [從資料庫產生]，然後按一下 [下一步]。

5. 在 [選擇資料連線] 頁面中，選取下列其中一個選項：

    - 若下拉式清單中有提供 AdventureWorksLT 範例資料庫的資料連接，請選取此資料連接。

    - 按一下 [新增連線]，建立與 AdventureWorksLT 資料庫的連線。

6. 在 [選擇資料連線] 頁面中，確定已選取 [將 App.Config 中的實體連線設定儲存為] 選項，然後按一下 [下一步]。

7. 在 [選擇您的資料庫物件] 頁面中，展開 [資料表]，然後選取 **SalesOrderHeader** 資料表。

8. 按一下 [完成] 。

## <a name="create-the-service"></a>建立服務

建立 WCF 資料服務，將實體資料模型中的資料公開給 WPF 應用程式：

1. 在 [專案] 功能表上，選取 [新增項目]。

2. 在 [已安裝的範本] 清單中，按一下 **Web**，然後選取 [WCF 資料服務] 專案項目。

3. 在 [ **名稱** ] 方塊中，輸入 `AdventureWorksService.svc` ，然後按一下 [ **新增**]。

     Visual Studio 將加入 `AdventureWorksService.svc` 至專案。

## <a name="configure-the-service"></a>設定服務

您必須設定服務，以處理您建立的實體資料模型：

1. 在程式 `AdventureWorks.svc` 代碼檔案中，以下列程式碼取代 **adventureworksservice.svc** 類別宣告。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb" id="Snippet1":::

     這段程式碼會更新 **adventureworksservice.svc** 類別，使其衍生自在 <xref:System.Data.Services.DataService%601> `AdventureWorksLTEntities` 實體資料模型中的物件內容類別上操作的。 該程式碼也會更新 `InitializeService` 方法，允許服務的用戶端對 `SalesOrderHeader` 實體具有完整的讀取/寫入存取權。

2. 建置專案，並確認專案建置無誤。

## <a name="create-the-wpf-client-application"></a>建立 WPF 用戶端應用程式

若要顯示 WCF 資料服務中的資料，請使用以服務為基礎的資料來源建立新的 WPF 應用程式。 稍後您將在此逐步解說中，將資料繫結控制項加入至應用程式。

1. 在 [方案總管] 中，以滑鼠右鍵按一下方案節點，然後按一下 [新增]，然後選取 [新增專案]。

2. 在 [新增專案] 對話方塊中，展開 [Visual C#] 或 [Visual Basic]，然後選取 [視窗]。

3. 選取 [WPF 應用程式] 專案範本。

4. 在 [名稱] 方塊中，鍵入 `AdventureWorksSalesEditor` 並按一下 [確定]。

   Visual Studio 將 `AdventureWorksSalesEditor` 專案加入至方案。

5. 按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。

   [資料來源] 視窗隨即開啟。

6. 在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。

   [資料來源組態精靈] 隨即開啟。

7. 在精靈的 [選擇資料來源類型] 頁面中，選取 [服務]，然後按一下 [下一步]。

8. 在  **[加入服務參考]** 對話方塊中，按一下  **[探索]**。

   Visual Studio 會在目前的解決方案中搜尋可用的服務，並新增 `AdventureWorksService.svc` 至 [ **服務** ] 方塊中的可用服務清單。

9. 在 [命名空間] 方塊中，鍵入 **AdventureWorksService**。

10. 在 [服務] 方塊中，按一下 **AdventureWorksService.svc**，然後按一下 [確定]。

    Visual Studio 會下載服務資訊，然後傳回 [資料來源組態精靈]。

11. 在 [新增服務參考] 頁面中按一下 [完成]。

    Visual Studio 會將代表服務所傳回之資料的節點，新增至 [資料來源] 視窗。

## <a name="define-the-user-interface"></a>定義使用者介面

透過在 WPF 設計工具中修改 XAML，將數個按鈕加入至視窗。 在此逐步解說的稍後內容中，您會加入程式碼，讓使用者使用這些按鈕檢視及更新銷售記錄。

1. 在 [方案總管] 中，按兩下 **MainWindow.xaml**。

   隨即會在 WPF 設計工具中開啟視窗。

2. 在設計工具的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 檢視中，在 `<Grid>` 標記之間加入下列程式碼：

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="525" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. 建置專案。

## <a name="create-the-data-bound-controls"></a>建立資料繫結控制項

將 `SalesOrderHeaders` 節點從 [ **資料來源** ] 視窗拖曳至設計工具，以建立顯示客戶記錄的控制項。

1. 在 [資料來源] 視窗中，按一下 [SalesOrderHeaders] 節點的下拉式功能表，然後選取 [詳細資料]。

2. 展開 [SalesOrderHeaders] 節點。

3. 在此範例中，某些欄位不會顯示，因此請按一下下列節點旁邊的下拉式功能表，然後選取 [無]：

    - **CreditCardApprovalCode**

    - **ModifiedDate**

    - **OnlineOrderFlag**

    - **RevisionNumber**

    - **rowguid**

    此動作可避免 Visual Studio 在下一個步驟中建立這些節點的資料繫結控制項。 在這個逐步解說中，假設終端使用者不需要查看此資料。

4. 從 [資料來源] 視窗將 [SalesOrderHeaders] 節點拖曳至包含按鈕之資料列下方的資料格列。

     Visual Studio 會產生 XAML 和程式碼，其可建立一組繫結至 [產品] 資料表之資料的控制項。 如需有關產生的 XAML 和程式碼的詳細資訊，請參閱將 [WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。

5. 在設計工具中，按一下 [Customer ID] 標籤旁邊的文字方塊。

6. 在 [屬性] 視窗中，選取 **IsReadOnly** 屬性旁邊的核取方塊。

7. 為下列每個文字方塊設定 **IsReadOnly** 屬性：

    - **採購單號碼**

    - **Sales Order ID**

    - **Sales Order Number**

## <a name="load-the-data-from-the-service"></a>從服務載入資料

使用服務 proxy 物件從服務載入銷售資料。 然後，將傳回的資料指派給 <xref:System.Windows.Data.CollectionViewSource> WPF 視窗中的資料來源。

1. 在設計師中，若要建立`Window_Loaded`事件處理常式，按兩下所讀取的文字：**MainWindow**。

2. 以下列程式碼取代事件處理常式。 確認您是使用開發電腦的本機主機位址，取代此程式碼中的 *localhost* 位址。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet2":::

## <a name="navigate-sales-records"></a>導覽銷售記錄

加入可讓使用者使用按鈕來滾動銷售記錄的程式碼 **\<** and **>** 。

1. 在設計工具中，按兩下 **<** 視窗介面上的按鈕。

     Visual Studio 會開啟程式碼後置檔案，並建立 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的新 `backButton_Click` 事件處理常式。

2. 將下列程式碼加入至產生的 `backButton_Click` 事件處理常式：

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet3":::

3. 返回設計工具，然後按兩下 **>** 按鈕。

     Visual Studio 會開啟程式碼後置檔案，並建立 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的新 `nextButton_Click` 事件處理常式。

4. 將下列程式碼加入至產生的 `nextButton_Click` 事件處理常式：

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet4":::

## <a name="save-changes-to-sales-records"></a>儲存銷售記錄的變更

新增程式碼，讓使用者可以使用 [儲存變更] 按鈕檢視及儲存銷售記錄的變更：

1. 在設計工具中，按兩下 [ **儲存變更** ] 按鈕。

     Visual Studio 會開啟程式碼後置檔案，並建立 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的新 `saveButton_Click` 事件處理常式。

2. 將下列程式碼加入至 `saveButton_Click` 事件處理常式。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet5":::

## <a name="test-the-application"></a>測試應用程式

建置並執行應用程式，以確認您可以檢視及更新客戶記錄：

1. 在 [ **組建** ] 功能表上，按一下 [ **建立方案**]。 確認方案建置無誤。

2. 按下 **Ctrl** + **F5**。

     Visual Studio 會啟動 **AdventureWorksService** 專案而不進行偵錯。

3. 在 [方案總管] 中，以滑鼠右鍵按一下 **AdventureWorksSalesEditor**。

4. 在右鍵功能表上 (內容功能表) 的 [ **Debug**] 下，按一下 [ **開始新實例**]。

     應用程式隨即執行。 驗證下列項目：

    - 這些文字方塊會從第一筆銷售記錄 (具有銷售訂單 ID **71774**) 的資料顯示不同欄位。

    - 您可以按一下 **>** 或 **<** 按鈕，以流覽其他銷售記錄。

5. 在其中一個銷售記錄中，在 [註解] 方塊中鍵入部分文字，然後按一下 [儲存變更]。

6. 關閉應用程式，然後從 Visual Studio 再次啟動應用程式。

7. 巡覽至您變更過的銷售記錄，並確認變更在您關閉及重新開啟應用程式之後仍然存在。

8. 關閉應用程式。

## <a name="next-steps"></a>下一步

完成此逐步解說後，您可以執行下列相關的工作：

- 了解如何使用 Visual Studio 中的 [資料來源] 視窗，將 WPF 控制項繫結程序至其他資料來源類型。 如需詳細資訊，請參閱將 [WPF 控制項系結至資料集](../data-tools/bind-wpf-controls-to-a-dataset.md)。

- 了解如何使用 Visual Studio 中的 [資料來源] 視窗，顯示 WPF 控制項中的相關資料 (也就是父子關聯性中的資料)。 如需詳細資訊，請參閱 [逐步解說：在 WPF 應用程式中顯示相關資料](../data-tools/display-related-data-in-wpf-applications.md)。

## <a name="see-also"></a>另請參閱

- [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [將 WPF 控制項繫結至資料集](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [WCF 總覽 ( .NET Framework) ](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Entity Framework 總覽 ( .NET Framework) ](/dotnet/framework/data/adonet/ef/overview)
- [資料系結總覽 ( .NET Framework) ](/dotnet/desktop-wpf/data/data-binding-overview)
