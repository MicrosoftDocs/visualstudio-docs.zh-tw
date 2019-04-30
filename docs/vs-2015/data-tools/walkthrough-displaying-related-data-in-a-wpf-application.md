---
title: 逐步解說：在 WPF 應用程式中顯示相關的資料 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: c7cd8a48092c39048d52a7ebe9cd27163ba32110
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424783"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>逐步解說：在 WPF 應用程式中顯示相關的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在本逐步解說中，您將建立 WPF 應用程式，以顯示具有父子式關聯性的資料庫資料表中的資料。 資料會封裝在 Entity Data Model 中的實體。 「 父 」 實體包含一份訂單的概觀資訊。 此實體的每一個屬性繫結至應用程式中不同的控制項。 子實體包含每筆訂單的詳細資料。 這組資料繫結至<xref:System.Windows.Controls.DataGrid>控制項。  
  
 這個逐步解說將說明下列工作：  
  
- 建立 WPF 應用程式和從 AdventureWorksLT 範例資料庫中的資料產生 Entity Data Model。  
  
- 建立一組資料繫結控制項，顯示一份訂單的概觀資訊。 您將從父實體建立控制項**資料來源** 視窗來**WPF 設計工具**。  
  
- 建立<xref:System.Windows.Controls.DataGrid>選取順序的每個顯示的相關詳細資料的控制項。 您建立控制項的子系實體**資料來源**視窗中的視窗**WPF 設計工具**。  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- 對執行中的 SQL Server 或 SQL Server Express (其中連結了 AdventureWorksLT 範例資料庫) 執行個體的存取權。 您可以下載 AdventureWorksLT 資料庫，從[CodePlex 網站](http://go.microsoft.com/fwlink/?linkid=87843)。  
  
  預先了解下列概念也有助於完成此逐步解說 (但非必要)：  
  
- 實體資料模型及 ADO.NET Entity Framework。 如需詳細資訊，請參閱 < [Entity Framework 概觀](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0)。  
  
- 使用 WPF 設計工具。 如需詳細資訊，請參閱 < [WPF 和 Silverlight Designer 概觀](http://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62)。  
  
- WPF 資料繫結。 如需詳細資訊，請參閱 [資料繫結概觀](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)。  
  
## <a name="creating-the-project"></a>建立專案  
 建立新的 WPF 專案，以顯示訂單記錄。  
  
#### <a name="to-create-a-new-wpf-project"></a>若要建立新的 WPF 專案  
  
1. 啟動 Visual Studio。  
  
2. 在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。  
  
3. 依序展開**Visual C#** 或是**Visual Basic**，然後選取**Windows**。  
  
4. 請確定 **.NET Framework 4**選取對話方塊頂端的下拉式方塊中。 <xref:System.Windows.Controls.DataGrid>您在本逐步解說中使用的控制項是僅適用於.NET Framework 4。  
  
5. 選取 [WPF 應用程式] 專案範本。  
  
6. 在 [名稱] 方塊中，輸入 `AdventureWorksOrdersViewer`。  
  
7. 按一下 [確定] 。  
  
     Visual Studio 會建立`AdventureWorksOrdersViewer`專案。  
  
## <a name="creating-an-entity-data-model-for-the-application"></a>Entity Data Model 建立應用程式  
 建立資料繫結控制項之前，您必須先定義應用程式的資料模型，並將其新增至 [資料來源] 視窗。 在此逐步解說中，資料模型會是 Entity Data Model。  
  
#### <a name="to-create-an-entity-data-model"></a>建立實體資料模型  
  
1. 在上**資料**功能表上，按一下**加入新的資料來源**以開啟**資料來源組態精靈**。  
  
2. 在上**選擇資料來源類型**頁面上，按一下**資料庫**，然後按一下**下一步**。  
  
3. 在上**選擇資料庫模型**頁面上，按一下**Entity Data Model**，然後按一下**下一步**。  
  
4. 在 [**選擇模型內容**頁面上，按一下**從資料庫產生**，然後按一下**下一步]**。  
  
5. 在 **選擇資料連接**頁面上，執行下列其中之一：  
  
   - 若下拉式清單中有提供 AdventureWorksLT 範例資料庫的資料連接，請選取此資料連接。  
  
      -或-  
  
   - 按一下 **新的連接**並建立 AdventureWorksLT 資料庫的連接。  
  
     請確定**將實體連接設定儲存在 App.Config 中，作為**選項已選取，然後再按一下**下一步**。  
  
6. 在 **選擇您的資料庫物件**頁面上，展開**資料表**，，然後選取下列資料表：  
  
   - **SalesOrderDetail**  
  
   - **SalesOrderHeader**  
  
7. 按一下 [ **完成**]。  
  
8. 建置專案。  
  
## <a name="creating-data-bound-controls-that-display-the-orders"></a>建立資料繫結控制項來顯示訂單  
 建立顯示訂單記錄拖曳控制項`SalesOrderHeaders`從實體**Zdroje dat**至 WPF 設計工具 視窗。  
  
#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>若要建立顯示訂單記錄的資料繫結控制項  
  
1. 在 [**方案總管] 中**，按兩下 MainWindow.xaml。  
  
    隨即會在 WPF 設計工具中開啟視窗。  
  
2. 編輯 XAML 因此**高度**並**寬度**屬性會設定為 800  
  
3. 在 [**資料來源**] 視窗中，按一下下拉式選單，如**SalesOrderHeaders**節點，然後選取**詳細資料**。  
  
4. 展開 [SalesOrderHeaders] 節點。  
  
5. 旁按一下下拉式選單**SalesOrderID** ，然後選取**ComboBox**。  
  
6. 每個下列子節點的**SalesOrderHeaders**節點、 按一下下拉式選單中下一步 [] 節點，然後選取**無**:  
  
   - **RevisionNumber**  
  
   - **OnlineOrderFlag**  
  
   - **ShipToAddressID**  
  
   - **BillToAddressID**  
  
   - **CreditCardApprovalCode**  
  
   - **SubTotal**  
  
   - **TaxAmt**  
  
   - **Freight**  
  
   - **rowguid**  
  
   - **ModifiedDate**  
  
     此動作可避免 Visual Studio 在下一個步驟中建立這些節點的資料繫結控制項。 在此逐步解說中，會假設終端使用者不需要看到此資料。  
  
7. 從**資料來源** 視窗中，拖曳**SalesOrderHeaders**節點中的視窗**WPF 設計工具**。  
  
    Visual Studio 會產生會建立一組中的資料繫結控制項的 XAML **SalesOrderHeaders**實體，並將資料載入的程式碼。 如需有關產生的 XAML 和程式碼的詳細資訊，請參閱 <<c0> [ 繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
8. 在設計工具中，按一下下拉式方塊旁邊**銷售單識別碼**標籤。  
  
9. 在 [屬性] 視窗中，選取 **IsReadOnly** 屬性旁邊的核取方塊。  
  
## <a name="creating-a-datagrid-that-displays-the-order-details"></a>建立資料格會顯示訂單詳細資料  
 建立<xref:System.Windows.Controls.DataGrid>顯示訂單詳細資料，藉由拖曳控制項`SalesOrderDetails`實體**Zdroje dat**至 WPF 設計工具 視窗。  
  
#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>若要建立顯示訂單詳細資料的 DataGrid  
  
1. 在 [**資料來源**] 視窗中，找出**SalesOrderDetails**子系的節點**SalesOrderHeaders**節點。  
  
   > [!NOTE]
   > 另外還有**SalesOrderDetails**的對等節點**SalesOrderHeaders**節點。 請確定您選取的子節點**SalesOrderHeaders**節點。  
  
2. 展開子**SalesOrderDetails**節點。  
  
3. 每個下列子節點的**SalesOrderDetails**節點、 按一下下拉式選單中下一步 [] 節點，然後選取**無**:  
  
   - **SalesOrderID**  
  
   - **SalesOrderDetailID**  
  
   - **rowguid**  
  
   - **ModifiedDate**  
  
     這個動作可防止 Visual Studio 包括此資料在<xref:System.Windows.Controls.DataGrid>您在下一個步驟中建立的控制項。 在此逐步解說中，會假設終端使用者不需要看到此資料。  
  
4. 從**資料來源** 視窗中，拖曳子系**SalesOrderDetails**節點中的視窗**WPF 設計工具**。  
  
    Visual Studio 會產生 XAML 來定義新的資料繫結<xref:System.Windows.Controls.DataGrid>控制與控制項出現在設計工具。 Visual Studio 也會更新所產生`GetSalesOrderHeadersQuery`程式碼後置檔案包含在資料中的方法**SalesOrderDetails**實體。  
  
## <a name="testing-the-application"></a>測試應用程式  
 建置並執行應用程式，以確認它會顯示訂單記錄。  
  
#### <a name="to-test-the-application"></a>若要測試應用程式  
  
1. 請按 **F5**。  
  
     隨即建置應用程式並執行。 驗證下列各項：  
  
    - **銷售單識別碼**下拉式方塊會顯示**71774**。 這是在實體中的第一個訂單識別碼。  
  
    - 您選取在每個訂單**銷售單識別碼**下拉式方塊中，會顯示詳細的訂單資訊<xref:System.Windows.Controls.DataGrid>。  
  
2. 關閉應用程式。  
  
## <a name="next-steps"></a>後續步驟  
 之後完成此逐步解說，了解如何使用**Zdroje dat**視窗在 Visual Studio 中要繫結 WPF 控制項新增至其他類型的資料來源。 如需詳細資訊，請參閱 <<c0> [ 繫結 WPF 控制項新增至 WCF data service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)並[繫結 WPF 控制項新增至資料集](../data-tools/bind-wpf-controls-to-a-dataset.md)。  
  
## <a name="see-also"></a>另請參閱  
 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [在 WPF 應用程式中顯示相關資料](../data-tools/display-related-data-in-wpf-applications.md)