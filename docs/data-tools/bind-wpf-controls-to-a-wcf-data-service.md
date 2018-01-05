---
title: "將 WPF 控制項繫結至 WCF 資料服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: ec13e17aac37a24e92732b9b052147c7d9faa916
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>將 WPF 控制項繫結至 WCF 資料服務
您將在此逐步解說中，建立包含資料繫結控制項的 WPF 應用程式。 這些控制項會繫結至封裝於 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]中的客戶記錄。 您也會加入按鈕，讓客戶可使用這些按鈕檢視及更新記錄。  
  
這個逐步解說將說明下列工作：  
  
- 建立從 AdventureWorksLT 範例資料庫中的資料產生的實體資料模型。  
  
- 建立[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]可公開實體資料模型，在 WPF 應用程式中的資料。  
  
- 建立一組資料繫結控制項項目從**資料來源**WPF 設計工具的視窗。  
  
- 建立可向前及向後巡覽客戶記錄的按鈕。  
  
- 建立按鈕，以將變更儲存到控制項中的資料到[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]和基礎資料來源。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>必要條件  
您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   對執行中的 SQL Server 或 SQL Server Express (其中連結了 AdventureWorksLT 範例資料庫) 執行個體的存取權。 您可以下載 AdventureWorksLT 資料庫從[CodePlex 網站上](http://go.microsoft.com/fwlink/?linkid=87843)。  
  
預先了解下列概念也有助於完成此逐步解說 (但非必要)：  
  
-   WCF 資料服務。 如需詳細資訊，請參閱[概觀](/dotnet/framework/data/wcf/wcf-data-services-overview)。  
  
-   [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]中的資料模型。  
  
-   實體資料模型及 ADO.NET Entity Framework。 如需詳細資訊，請參閱[Entity Framework 概觀](/dotnet/framework/data/adonet/ef/overview)。  
  
-   WPF 資料繫結。 如需詳細資訊，請參閱 [資料繫結概觀](/dotnet/framework/wpf/data/data-binding-overview)。  
  
## <a name="create-the-service-project"></a>建立服務專案  
建立 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]的專案以開始此逐步解說。  
  
#### <a name="to-create-the-service-project"></a>建立服務專案  
  
1.  啟動 Visual Studio。  
  
2.  在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。  
  
3.  展開**Visual C#**或**Visual Basic**，然後選取**Web**。  
  
4.  選取 [ASP.NET Web 應用程式] 專案範本。  
  
5.  在**名稱**方塊中，輸入`AdventureWorksService`按一下**確定**。  
  
     Visual Studio 會建立`AdventureWorksService`專案。  
  
6.  在**方案總管 中**，以滑鼠右鍵按一下**Default.aspx**選取**刪除**。 在此逐步解說中不需要此檔案。  
  
## <a name="create-an-entity-data-model-for-the-service"></a>建立實體資料模型服務  
若要使用 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]將資料公開給應用程式，您必須定義服務的資料模型。 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]支援兩種類型的資料模型： 實體資料模型，與使用實作的 common language runtime (CLR) 物件所定義的自訂資料模型<xref:System.Linq.IQueryable%601>介面。 在此逐步解說中，您要建立資料模型的實體資料模型。  
  
#### <a name="to-create-an-entity-data-model"></a>建立實體資料模型  
  
1.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
2.  在已安裝的範本清單中，按一下 **資料**，然後選取**ADO.NET 實體資料模型**專案項目。  
  
3.  將名稱變更為`AdventureWorksModel.edmx`，然後按一下**新增**。  
  
     **實體資料模型**精靈 隨即開啟。  
  
4.  在**選擇模型內容**頁面上，按一下**從資料庫產生**，然後按一下**下一步**。  
  
5.  在**選擇資料連接**頁面上，選取下列選項之一：  
  
    -   若下拉式清單中有提供 AdventureWorksLT 範例資料庫的資料連接，請選取此資料連接。  
  
    -   按一下**新連線**，以及建立與 AdventureWorksLT 資料庫的連線。  
  
6.  在**選擇資料連接**頁面上，請確定**將實體連接設定儲存為 App.Config 中**選項已選取，然後按一下 **下一步**。  
  
7.  在**選擇您的資料庫物件**頁面上，展開**資料表**，然後選取**SalesOrderHeader**資料表。  
  
8.  按一下 [ **完成**]。  
  
## <a name="create-the-service"></a>建立服務  
建立[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]以公開實體資料模型，在 WPF 應用程式中的資料。  
  
#### <a name="to-create-the-service"></a>建立服務  
  
1.  在**專案**功能表上，選取**加入新項目**。  
  
2.  在已安裝的範本清單中，按一下  **Web**，然後選取**WCF 資料服務**專案項目。  
  
3.  在**名稱**方塊中，輸入`AdventureWorksService.svc`，然後按一下**新增**。  
  
     Visual Studio 會加入`AdventureWorksService.svc`至專案。  
  
## <a name="configure-the-service"></a>設定服務  
您必須設定服務，以處理您建立的實體資料模型。  
  
#### <a name="to-configure-the-service"></a>設定服務  
  
1.  在`AdventureWorks.svc`程式碼檔案，取代`AdventureWorksService`類別宣告為下列程式碼。  
  
     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]  
  
     此程式碼會更新`AdventureWorksService`類別，使其衍生自<xref:System.Data.Services.DataService%601>，對`AdventureWorksLTEntities`物件內容類別，在您實體資料模型。 該程式碼也會更新 `InitializeService` 方法，允許服務的用戶端對 `SalesOrderHeader` 實體具有完整的讀取/寫入存取權。  
  
2.  建置專案，並確認專案建置無誤。  
  
## <a name="create-the-wpf-client-application"></a>建立 WPF 用戶端應用程式  
若要從 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]顯示資料，請使用以服務為基礎的資料來源，建立新的 WPF 應用程式。 稍後您將在此逐步解說中，將資料繫結控制項加入至應用程式。  
  
#### <a name="to-create-the-wpf-client-application"></a>建立 WPF 用戶端應用程式  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下方案節點，按一下**新增**，然後選取**新專案**。  
  
2.  在**新專案**] 對話方塊中，展開 [ **Visual C#**或**Visual Basic**，然後選取**Windows**。  
  
3.  選取**WPF 應用程式**專案範本。  
  
4.  在**名稱**方塊中，輸入`AdventureWorksSalesEditor`，然後按一下**確定**。  
  
     Visual Studio 會加入`AdventureWorksSalesEditor`專案加入方案。  
  
5.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。  
  
     **資料來源**視窗隨即開啟。  
  
6.  在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。  
  
     **資料來源組態**精靈 隨即開啟。  
  
7.  在**選擇資料來源類型**頁面的精靈中，選取**服務**，然後按一下 **下一步**。  
  
8.  在**加入服務參考**對話方塊中，按一下 **探索**。  
  
     Visual Studio 會搜尋目前方案中的可用服務，並將`AdventureWorksService.svc`中的可用服務清單**服務**方塊。  
  
9. 在**命名空間**方塊中，輸入`AdventureWorksService`。  
  
10. 在**服務**方塊中，按一下**AdventureWorksService.svc**，然後按一下 **確定**。  
  
     Visual Studio 會下載服務資訊，，然後傳回**資料來源組態**精靈。  
  
11. 在**加入服務參考**頁面上，按一下**完成**。  
  
     Visual Studio 會將代表服務所傳回的資料節點**資料來源**視窗。  
  
## <a name="define-the-user-interface-of-the-window"></a>定義視窗的使用者介面  
透過在 WPF 設計工具中修改 XAML，將數個按鈕加入至視窗。 在此逐步解說的稍後內容中，您會加入程式碼，讓使用者使用這些按鈕檢視及更新銷售記錄。  
  
#### <a name="to-create-the-window-layout"></a>建立視窗配置  
  
1.  在**方案總管 中**，連按兩下**MainWindow.xaml**。  
  
     隨即會在 WPF 設計工具中開啟視窗。  
  
2.  在設計工具的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 檢視中，在 `<Grid>` 標記之間加入下列程式碼：  
  
    ```xaml  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="525" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  建置專案。  
  
## <a name="create-the-data-bound-controls"></a>建立資料繫結控制項  
建立顯示客戶記錄拖曳控制項`SalesOrderHeaders`節點從**資料來源**至設計工具 視窗。  
  
#### <a name="to-create-the-data-bound-controls"></a>建立資料繫結控制項  
  
1.  在**資料來源**視窗中，按一下下拉式選單，如**SalesOrderHeaders**節點，然後選取**詳細資料**。  
  
2.  展開**SalesOrderHeaders**節點。  
  
3.  此範例中，某些欄位將不會顯示，因此按下列節點旁邊的下拉式清單功能表然後選取**無**:  
  
    -   **CreditCardApprovalCode**  
  
    -   **ModifiedDate**  
  
    -   **OnlineOrderFlag**  
  
    -   **RevisionNumber**  
  
    -   **rowguid**  
  
    此動作可避免 Visual Studio 在下一個步驟中建立這些節點的資料繫結控制項。 本逐步解說，假設使用者不需要看到此資料。  
  
4.  從**資料來源** 視窗中，拖曳**SalesOrderHeaders**包含按鈕的資料列底下的方格資料列的節點。  
  
     Visual Studio 會產生 XAML 和程式碼會建立一組控制項中的資料繫結**產品**資料表。 如需產生的 XAML 和程式碼的詳細資訊，請參閱[繫結 WPF 控制項加入 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。  
  
5.  在設計師中，按一下文字方塊旁邊**客戶 ID**標籤。  
  
6.  在**屬性**視窗中，選取旁的核取方塊**IsReadOnly**屬性。  
  
7.  設定**IsReadOnly**下列文字方塊中的每個屬性：  
  
    -   **訂單號碼**  
  
    -   **銷售訂單識別碼**  
  
    -   **銷售訂單號碼**  
  
## <a name="load-the-data-from-the-service"></a>從服務載入資料  
您可以使用服務 proxy 物件來從服務載入銷售資料。 然後將傳回的資料指派給資料來源<xref:System.Windows.Data.CollectionViewSource>WPF 視窗中。  
  
#### <a name="to-load-the-data-from-the-service"></a>從服務載入資料  
  
1.  在設計師中，若要建立`Window_Loaded`事件處理常式中，按兩下所讀取的文字： **MainWindow**。  
  
2.  以下列程式碼取代事件處理常式。 請確定您取代*localhost*這個程式碼中的位址與開發電腦上的本機主機位址。  
  
     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]  
  
## <a name="navigate-sales-records"></a>巡覽銷售記錄  
加入程式碼，可讓使用者使用捲動銷售記錄 **\<** 和 **>** 按鈕。  
  
#### <a name="to-enable-users-to-navigate-sales-records"></a>讓使用者巡覽銷售記錄  
  
1.  在設計師中，按兩下 **<** 視窗介面上的按鈕。  
  
     Visual Studio 會開啟程式碼後置檔案，並建立新`backButton_Click`事件處理常式<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
2.  將下列程式碼加入至產生的 `backButton_Click` 事件處理常式：  
  
     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]  
  
3.  回到設計工具中，然後按兩下 **>**   按鈕。  
  
     Visual Studio 會開啟程式碼後置檔案，並建立新`nextButton_Click`事件處理常式<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
4.  將下列程式碼加入至產生的 `nextButton_Click` 事件處理常式：  
  
     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]  
  
## <a name="saving-changes-to-sales-records"></a>正在儲存銷售記錄的變更  
加入程式碼，可讓使用者檢視及儲存銷售記錄的變更，使用**儲存變更** 按鈕。  
  
#### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>加入可儲存銷售記錄變更的功能  
  
1.  在設計師中，按兩下**儲存變更** 按鈕。  
  
     Visual Studio 會開啟程式碼後置檔案，並建立新`saveButton_Click`事件處理常式<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
2.  將下列程式碼加入至 `saveButton_Click` 事件處理常式。  
  
     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]  
  
## <a name="testing-the-application"></a>測試應用程式  
建置並執行應用程式，以確認您可以檢視及更新客戶記錄。  
  
#### <a name="to-test-the-application"></a>若要測試應用程式  
  
1.  在**建置**功能表上，按一下 **建置方案**。 確認方案建置無誤。  
  
2.  按**Ctrl + F5**。  
  
     Visual Studio 會啟動**AdventureWorksService**專案，但不偵錯它。  
  
3.  在**方案總管 中**，以滑鼠右鍵按一下**AdventureWorksSalesEditor**專案。  
  
4.  在內容功能表中，在**偵錯**，按一下 **開始新執行個體**。  
  
     應用程式隨即執行。 驗證下列各項：  
  
    -   文字方塊中顯示不同欄位的資料，從第一筆銷售記錄，具有銷售訂單 ID **71774**。  
  
    -   您可以按一下 **>** 或 **<** 按鈕，巡覽其他銷售記錄。  
  
5.  在其中一個銷售記錄，請輸入某些文字**註解**方塊，然後再按一下**儲存變更**。  
  
6.  關閉應用程式，然後從 Visual Studio 再次啟動應用程式。  
  
7.  巡覽至您變更過的銷售記錄，並確認變更在您關閉及重新開啟應用程式之後仍然存在。  
  
8.  關閉應用程式。  
  
## <a name="next-steps"></a>後續步驟  
完成此逐步解說後，您可以執行下列相關的工作：  
  
-   了解如何使用**資料來源**WPF 的繫結的 Visual Studio 中的視窗控制項為其他類型的資料來源。 如需詳細資訊，請參閱[繫結 WPF 控制項至資料集](../data-tools/bind-wpf-controls-to-a-dataset.md)。  
  
-   了解如何使用**資料來源**WPF 控制項中顯示相關的資料 （也就是父子式關聯性中的資料） 的 Visual Studio 中的視窗。 如需詳細資訊，請參閱[逐步解說： 在 WPF 應用程式中顯示相關資料](../data-tools/display-related-data-in-wpf-applications.md)。  
  
## <a name="see-also"></a>另請參閱
[將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)   
[將 WPF 控制項繫結至資料集](../data-tools/bind-wpf-controls-to-a-dataset.md)   
[WCF 概觀 (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)   
[Entity Framework 概觀 (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)  
[資料繫結概觀 (.NET Framework)](/dotnet/framework/wpf/data/data-binding-overview)