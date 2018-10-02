---
title: 逐步解說： 以 Dataset 設計工具建立資料集 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7c17a93a5d250ce620c37a2a0a89472bf760750b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489657"
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>逐步解說：以 DataSet 設計工具建立資料集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在本逐步解說中您將建立資料集，使用**Dataset 設計工具**。 它會帶您完成建立新專案，並加入新的程序**資料集**給它的項目。 您將了解如何建立根據資料庫中的資料表，而不需使用精靈的資料表。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立新**Windows 應用程式**專案。  
  
-   新增空**資料集**項目加入專案。  
  
-   建立及設定您的應用程式中的資料來源，建置具有資料集**Dataset 設計工具**。  
  
-   建立 Northwind 資料庫中的連線**伺服器總管**。  
  
-   使用 Tableadapter 建立資料表，在基礎資料庫中資料表的資料集。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您需要：  
  
-   Northwind 範例資料庫的存取權 (SQL Server 或 Access 版本)。 如需詳細資訊，請參閱 <<c0> [ 如何： 安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## <a name="creating-a-new-windows-application-project"></a>建立新的 Windows 應用程式專案  
  
#### <a name="to-create-a-new-windows-application-project"></a>建立新的 Windows 應用程式專案  
  
1.  從**檔案** 功能表中，建立新的專案。  
  
2.  選擇程式設計語言**專案類型**窗格。  
  
3.  按一下  **Windows 應用程式**中**範本**窗格。  
  
4.  將專案命名為`DatasetDesignerWalkthrough`，然後按一下 **[確定]**。  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會將專案加入至**方案總管 中**並顯示新的表單設計工具中。  
  
## <a name="adding-a-new-dataset-to-the-application"></a>將新的資料集新增至應用程式  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>將新的資料集項目加入至專案  
  
1.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
     [新增項目] 對話方塊隨即出現。  
  
2.  在 [**範本**的方塊**加入新項目**] 對話方塊中，按一下**資料集**。  
  
3.  命名資料集`NorthwindDataset`，然後按一下**新增**。  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會加入檔案，稱為**NorthwindDataset.xsd**專案中開啟它並**Dataset 設計工具**。  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>在 [伺服器總管] 中建立資料連接  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>若要建立 Northwind 資料庫的連接  
  
1.  在 **檢視**功能表上，按一下**伺服器總管**。  
  
2.  在 [**伺服器總管**，按一下**連接到資料庫**] 按鈕。  
  
3.  建立 Northwind 範例資料庫的連接。  
  
    > [!NOTE]
    >  您可以連接到 SQL Server 或 Access 版本的 Northwind 在此逐步解說。  
  
## <a name="creating-the-tables-in-the-dataset"></a>建立資料集內的資料表  
 本章節將說明如何將資料表加入至資料集。  
  
#### <a name="to-create-the-customers-table"></a>若要建立 Customers 資料表  
  
1.  展開您在中建立的資料連接**伺服器總管**，然後展開**資料表**節點。  
  
2.  拖曳**客戶**資料表中**伺服器總管**拖曳至**Dataset 設計工具**。  
  
     A**客戶**資料表並**CustomersTableAdapter**加入資料集。  
  
#### <a name="to-create-the-orders-table"></a>若要建立 Orders 資料表  
  
-   拖曳**訂單**資料表中**伺服器總管**拖曳至**Dataset 設計工具**。  
  
     **訂單**資料表格**OrdersTableAdapter**，和資料之間的關聯性**客戶**並**訂單**資料表會加入至資料集。  
  
#### <a name="to-create-the-orderdetails-table"></a>若要建立 [OrderDetails] 資料表  
  
-   拖曳**訂單明細**資料表中**伺服器總管**拖曳至**Dataset 設計工具**。  
  
     **訂單詳細資料**資料表格**順序 DetailsTableAdapter**，和之間的資料關聯**訂單**並**訂單詳細資料**資料表會加入至資料集。  
  
## <a name="next-steps"></a>後續步驟  
  
### <a name="to-add-functionality-to-your-application"></a>加入應用程式的功能  
  
-   儲存的資料集。  
  
-   選取中的項目**Zdroje dat**視窗並將其拖曳到表單上。 如需詳細資訊，請參閱 <<c0> [ 繫結 Windows Form 控制項加入 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)。  
  
-   加入 Tableadapter 的更多查詢。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)。  
  
-   將驗證邏輯加入<xref:System.Data.DataTable.ColumnChanging>或<xref:System.Data.DataTable.RowChanging>事件的資料集內的資料表。 如需詳細資訊，請參閱 <<c0> [ 驗證資料集中](../data-tools/validate-data-in-datasets.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料逐步解說](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [連接到 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [將資料擷取至您的應用程式](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [儲存資料](../data-tools/saving-data.md)