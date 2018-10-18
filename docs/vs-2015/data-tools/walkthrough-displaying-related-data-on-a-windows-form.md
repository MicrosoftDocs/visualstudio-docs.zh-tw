---
title: 逐步解說： 顯示 Windows Form 上的相關的資料 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- master-details lists, displaying on Windows Forms
- data [Visual Studio], master-details
- displaying tables, related data
- displaying table data
- displaying table information
ms.assetid: fc4b9055-2bf3-4028-8aad-9489820d69f6
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 882c8229c105920efe247a54e9525a262e6a3246
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282668"
---
# <a name="walkthrough-displaying-related-data-on-a-windows-form"></a>逐步解說：顯示 Windows Form 上的相關資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在許多應用程式情節中，您會想要使用來自多張資料表的資料 (通常是相關資料表中的資料)。 亦即，您想要使用父子式關聯性。 例如，您可能想要建立表單，而在表單中，選取客戶記錄會顯示該客戶的訂單。 在表單上顯示相關記錄的方式是將子 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 的 <xref:System.Windows.Forms.BindingSource> 屬性設定為父 <xref:System.Windows.Forms.BindingSource> (非子資料表)，以及將子 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 的 <xref:System.Windows.Forms.BindingSource> 屬性設定為將父資料表與子資料表繫結在一起的資料關聯。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立**Windows 應用程式**專案。  
  
-   建立和設定應用程式中的資料集為基礎`Customers`並`Orders`在 Northwind 資料庫中使用的資料表[資料來源組態精靈](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)。  
  
-   加入控制項，以顯示 `Customers` 資料表中的資料。  
  
-   加入控制項，以根據選取的 `Orders` 顯示 `Customer`。  
  
-   選取不同的客戶，並驗證是否針對所選客戶顯示正確的訂單，藉以測試應用程式。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您需要：  
  
-   Northwind 範例資料庫的存取權。 若要設定範例資料庫，請參閱[如何： 安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立**Windows 應用程式**。  
  
#### <a name="to-create-the-windows-application-project"></a>建立 Windows 應用程式專案  
  
1.  從**檔案** 功能表中，建立新的專案。  
  
2.  將專案命名為 `RelatedDataWalkthrough`。  
  
3.  選取  **Windows 應用程式**然後按一下**確定**。 如需詳細資訊，請參閱 <<c0> [ 用戶端應用程式](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)。  
  
     **RelatedDataWalkthrough**建立專案並將其加入至**方案總管 中**。  
  
## <a name="creating-the-data-source"></a>建立資料來源  
 此步驟根據 Northwind 範例資料庫中的 `Customers` 和 `Orders` 資料表來建立資料集。  
  
#### <a name="to-create-the-data-source"></a>若要建立資料來源  
  
1.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。  
  
2.  在 **資料來源**視窗中，選取**加入新的資料來源**來啟動**資料來源組態精靈**。  
  
3.  請選取 [ **選擇資料來源類型** ] 頁面上的 [ **資料庫** ]，再按 [ **下一步**]。  
  
4.  在 **選擇您的資料連接**頁面上，執行下列其中之一：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
         -或-  
  
    -   選取 [**新的連線**來啟動**加入/修改連接**] 對話方塊。  
  
5.  如果您的資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下**下一步**。  
  
6.  按一下 **下一步**上**將連接字串儲存到應用程式組態檔**頁面。  
  
7.  依序展開**資料表**上的節點**選擇您的資料庫物件**頁面。  
  
8.  選取 **客戶**並**訂單**資料表，然後再按一下**完成**。  
  
     **NorthwindDataSet**新增至您的專案並**客戶**資料表會出現在**Zdroje dat**視窗。  
  
## <a name="creating-controls-to-display-data-from-the-customers-table"></a>建立控制項以顯示客戶資料表的資料  
  
#### <a name="to-create-controls-to-display-the-customer-data-parent-records"></a>若要建立控制項以顯示客戶資料 (父資料錄)  
  
1.  在 **資料來源**視窗中，選取**客戶**資料表，然後按一下下拉箭號。  
  
2.  選擇**詳細資料**從功能表。  
  
3.  主**客戶**從節點**Zdroje dat**視窗的頂端**Form1**。  
  
     會在表單上顯示具有描述性標籤的資料繫結控制項，以及巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>)。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)， [CustomersTableAdapter](../data-tools/tableadapter-overview.md)， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>會出現在元件匣。  
  
## <a name="creating-controls-to-display-data-from-the-orders-table"></a>建立控制項以顯示訂單資料表的資料  
 ![顯示關聯性的資料來源視窗](../data-tools/media/datasources2.gif "DataSources2")  
  
#### <a name="to-create-controls-to-display-the-orders-for-each-customer-child-records"></a>若要建立控制項以顯示每位客戶的訂單 (子資料錄)  
  
-   在**資料來源** 視窗中，展開**客戶**節點，然後選取中的最後一個資料行**客戶**資料表，其為可展開**訂單**節點，並將它拖曳到底部**Form1**。  
  
     <xref:System.Windows.Forms.DataGridView> 隨即加入至表單中，而且新的 <xref:System.Windows.Forms.BindingSource> (`OrdersBindingSource`) 和 TableAdapter (`OrdersTableAdapter`)也會加入至元件匣。  
  
    > [!NOTE]
    >  開啟[屬性 視窗](../ide/reference/properties-window.md)，然後選取**OrdersBindingSource**。 檢查 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 和 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 屬性，查看如何設定繫結以顯示相關記錄。 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 設定為 `CustomersBindingSource` (父資料表的 <xref:System.Windows.Forms.BindingSource>)，而不是 `Orders` 資料表。 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 屬性設定為 `FK_Orders_Customers`，它是使這些資料表互相產生關聯的 <xref:System.Data.DataRelation> 物件名稱。  
  
## <a name="testing-the-application"></a>測試應用程式  
  
#### <a name="to-test-the-application"></a>若要測試應用程式  
  
1.  按 F5 執行應用程式。  
  
2.  選取使用不同的客戶**CustomersBindingNavigator**若要確認正確的訂單會顯示在<xref:System.Windows.Forms.DataGridView>。  
  
## <a name="next-steps"></a>後續步驟  
 根據應用程式的需求而定，在建立主從式 (Master-Detail) 表單後，可能會有幾個想要執行的步驟。 其中一個您可以對這個逐步解說進行加強的部分是：  
  
-   將參數化加入至 `Customers` 資料表，以篩選 `Customers` 記錄。 若要這樣做，請選取 顯示資料的任何控制項`Customers`資料表中，按一下 智慧標籤，並選擇**加入查詢**。 完成[搜尋準則產生器 對話方塊](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d)。 如需詳細資訊，請參閱 <<c0> [ 如何： 將參數化查詢加入至 Windows Forms 應用程式](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416)。  
  
## <a name="see-also"></a>另請參閱  
 [資料逐步解說](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [加入新的資料來源](../data-tools/add-new-data-sources.md)   
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [如何： 顯示相關的資料在 Windows Forms 應用程式](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)   
 [BindingSource 元件概觀](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)   
 [BindingNavigator 控制項概觀](http://msdn.microsoft.com/library/4423eede-f8d1-4d02-822f-5bf8432680d0)