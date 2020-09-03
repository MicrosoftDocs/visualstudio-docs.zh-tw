---
title: 逐步解說：顯示 WPF 應用程式中的相關資料 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 8116d4ab4a2f20f79f3849ae7f8b324af9832dd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850245"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>逐步解說：顯示 WPF 應用程式中的相關資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在這個逐步解說中，您將建立 WPF 應用程式，以顯示具有父/子關聯性之資料庫資料表中的資料。 資料會封裝在實體資料模型的實體中。 父實體包含一組訂單的總覽資訊。 此實體的每個屬性都會系結至應用程式中的不同控制項。 子實體包含每個訂單的詳細資料。 這組資料會系結至 <xref:System.Windows.Controls.DataGrid> 控制項。

 本逐步解說將說明下列工作：

- 建立 WPF 應用程式，以及從 AdventureWorksLT 範例資料庫中的資料產生的實體資料模型。

- 建立一組資料繫結控制項，以顯示一組訂單的總覽資訊。 您可以從 [ **資料來源** ] 視窗將父實體拖曳至 **WPF 設計**工具，藉以建立控制項。

- 建立 <xref:System.Windows.Controls.DataGrid> 可顯示每個所選訂單之相關詳細資料的控制項。 您可以從 [ **資料來源** ] 視窗中，將子實體拖曳至 **WPF 設計**工具中的視窗，藉以建立控制項。

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

- 對執行中的 SQL Server 或 SQL Server Express (其中連結了 AdventureWorksLT 範例資料庫) 執行個體的存取權。 您可以從 [CodePlex 網站](https://codeplex.com/SqlServerSamples)下載 AdventureWorksLT 資料庫。

  預先了解下列概念也有助於完成此逐步解說 (但非必要)：

- 實體資料模型及 ADO.NET Entity Framework。 如需詳細資訊，請參閱 [Entity Framework 總覽](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0)。

- 使用 WPF 設計工具。 如需詳細資訊，請參閱 [WPF 和 Silverlight 設計工具總覽](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62)。

- WPF 資料繫結。 如需詳細資訊，請參閱資料系結 [總覽](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)。

## <a name="creating-the-project"></a>建立專案
 建立新的 WPF 專案，以顯示訂單記錄。

#### <a name="to-create-a-new-wpf-project"></a>若要建立新的 WPF 專案

1. 啟動 Visual Studio。

2. 在 **[檔案]** 功能表上，指向 **[開新檔案]** ，然後按一下 **[專案]** 。

3. 展開 [ **Visual c #** ] 或 [ **Visual Basic**]，然後選取 [ **Windows**]。

4. 請確定已在對話方塊頂端的下拉式方塊中選取 **.NET Framework 4** 。 <xref:System.Windows.Controls.DataGrid>您在此逐步解說中使用的控制項僅適用于 .NET Framework 4。

5. 選取 [WPF 應用程式]**** 專案範本。

6. 在 [名稱]**** 方塊中，輸入 `AdventureWorksOrdersViewer`。

7. 按一下 [確定]  。

     Visual Studio 建立 `AdventureWorksOrdersViewer` 專案。

## <a name="creating-an-entity-data-model-for-the-application"></a>建立應用程式的實體資料模型
 建立資料繫結控制項之前，您必須先定義應用程式的資料模型，並將其新增至 [資料來源]**** 視窗。 在這個逐步解說中，資料模型是實體資料模型。

#### <a name="to-create-an-entity-data-model"></a>建立實體資料模型

1. 在 [ **資料** ] 功能表上，按一下 [ **加入新資料來源** ] 以開啟 [ **資料來源設定]**。

2. 在 [ **選擇資料來源類型** ] 頁面上，按一下 [ **資料庫**]，然後按 **[下一步]**。

3. 在 [ **選擇資料庫模型** ] 頁面上，按一下 [ **實體資料模型**，然後按 **[下一步]**。

4. 在 [ **選擇模型內容** ] 頁面上，按一下 [ **從資料庫產生**]，然後按 **[下一步]**。

5. 在 [ **選擇您的資料連線** ] 頁面上，執行下列其中一項：

   - 若下拉式清單中有提供 AdventureWorksLT 範例資料庫的資料連接，請選取此資料連接。

      -或-

   - 按一下 [ **新增連接** ]，並建立與 AdventureWorksLT 資料庫的連接。

     確定已選取 [ **在 App.Config 中儲存實體連接設定** ] 選項，然後按 **[下一步]**。

6. 在 [ **選擇您的資料庫物件** ] 頁面上，展開 [ **資料表]**，然後選取下列資料表：

   - **SalesOrderDetail**

   - **SalesOrderHeader**

7. 按一下 [完成]  。

8. 建置專案。

## <a name="creating-data-bound-controls-that-display-the-orders"></a>建立顯示訂單的資料繫結控制項
 `SalesOrderHeaders`從 [**資料來源**] 視窗將實體拖曳至 WPF 設計工具，以建立顯示訂單記錄的控制項。

#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>若要建立資料繫結控制項以顯示訂單記錄

1. 在 **方案總管**中，按兩下 [MainWindow]。

    隨即會在 WPF 設計工具中開啟視窗。

2. 編輯 XAML，讓 **高度** 和 **寬度** 屬性設定為800

3. 在 [ **資料來源** ] 視窗中，按一下 [ **salesorderheaders]** ] 節點的下拉式功能表，然後選取 [ **詳細**資料]。

4. 展開 [SalesOrderHeaders]**** 節點。

5. 按一下 [ **SalesOrderID** ] 旁邊的下拉式功能表，然後選取 [ **ComboBox**]。

6. 針對 **salesorderheaders]** 節點的下列子節點，按一下節點旁邊的下拉式功能表，然後選取 [ **無**]：

   - **RevisionNumber**

   - **OnlineOrderFlag**

   - **ShipToAddressID**

   - **BillToAddressID**

   - **CreditCardApprovalCode**

   - **次 全 切除**

   - **TaxAmt**

   - **Freight**

   - **rowguid**

   - **ModifiedDate**

     此動作可避免 Visual Studio 在下一個步驟中建立這些節點的資料繫結控制項。 在此逐步解說中，會假設終端使用者不需要看到此資料。

7. 從 [ **資料來源** ] 視窗中，將 [ **salesorderheaders]** ] 節點拖曳至 **WPF 設計**工具中的視窗。

    Visual Studio 會產生 XAML，其會建立一組系結至 **salesorderheaders]** 實體中資料的控制項，以及用來載入資料的程式碼。 如需有關產生的 XAML 和程式碼的詳細資訊，請參閱將 [WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。

8. 在設計工具中，按一下 [ **銷售訂單 ID** ] 標籤旁邊的下拉式方塊。

9. 在 [屬性]**** 視窗中，選取 **IsReadOnly** 屬性旁邊的核取方塊。

## <a name="creating-a-datagrid-that-displays-the-order-details"></a>建立顯示訂單詳細資料的 DataGrid
 藉 <xref:System.Windows.Controls.DataGrid> 由將 `SalesOrderDetails` 實體從 [ **資料來源** ] 視窗拖曳至 WPF 設計工具，建立顯示訂單詳細資料的控制項。

#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>建立顯示訂單詳細資料的 DataGrid

1. 在 [**資料來源**] 視窗中，找出屬於**salesorderheaders]** 節點之子系的**SalesOrderDetails**節點。

   > [!NOTE]
   > 另外還有一個 **SalesOrderDetails** 節點，也就是 **salesorderheaders]** 節點的對等節點。 請確定您選取的是 **salesorderheaders]** 節點的子節點。

2. 展開子 **SalesOrderDetails** 節點。

3. 針對 **SalesOrderDetails** 節點的下列子節點，按一下節點旁邊的下拉式功能表，然後選取 [ **無**]：

   - **SalesOrderID**

   - **SalesOrderDetailID**

   - **rowguid**

   - **ModifiedDate**

     此動作可防止 Visual Studio 在 <xref:System.Windows.Controls.DataGrid> 您于下一個步驟中所建立的控制項中包含此資料。 在此逐步解說中，會假設終端使用者不需要看到此資料。

4. 從 [ **資料來源** ] 視窗中，將 [子 **SalesOrderDetails** ] 節點拖曳至 **WPF 設計**工具中的視窗。

    Visual Studio 會產生 XAML 來定義新的資料繫結 <xref:System.Windows.Controls.DataGrid> 控制項，而且控制項會出現在設計工具中。 Visual Studio 也會更新程式 `GetSalesOrderHeadersQuery` 代碼後端檔案中產生的方法，以將資料包含在 **SalesOrderDetails** 實體中。

## <a name="testing-the-application"></a>測試應用程式
 建立並執行應用程式，以確認它會顯示訂單記錄。

#### <a name="to-test-the-application"></a>若要測試應用程式

1. 按 **F5**。

     隨即建置應用程式並執行。 驗證下列項目：

    - [ **銷售訂單識別碼** ] 下拉式方塊會顯示 **71774**。 這是實體中的第一個訂單識別碼。

    - 針對您在 [ **銷售訂單識別碼** ] 下拉式方塊中選取的每個訂單，會在中顯示詳細的訂單資訊 <xref:System.Windows.Controls.DataGrid> 。

2. 關閉應用程式。

## <a name="next-steps"></a>後續步驟
 完成此逐步解說之後，您將瞭解如何使用 Visual Studio 中的 [ **資料來源** ] 視窗，將 WPF 控制項系結至其他資料來源類型。 如需詳細資訊，請參閱將 [wpf 控制項系結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) ，並將 [wpf 控制項系結至資料集](../data-tools/bind-wpf-controls-to-a-dataset.md)。

## <a name="see-also"></a>另請參閱
 [將 wpf 控制項系結至 Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)在[wpf 應用程式中顯示相關資料](../data-tools/display-related-data-in-wpf-applications.md)的資料
