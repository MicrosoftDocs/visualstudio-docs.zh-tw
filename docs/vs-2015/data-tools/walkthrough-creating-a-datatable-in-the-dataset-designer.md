---
title: 逐步解說： 以 Dataset 設計工具建立 DataTable |Microsoft Docs
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
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 832dba200fca438d000bae101381389ea20cfb17
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488240"
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>逐步解說：以 DataSet 設計工具建立 DataTable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說說明如何建立<xref:System.Data.DataTable>（不含 TableAdapter) 使用**Dataset 設計工具**。 如需建立包含 Tableadapter 的資料表資訊，請參閱[建立和設定 Tableadapter](../data-tools/create-and-configure-tableadapters.md)。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立新的 Windows 應用程式專案  
  
-   將新的資料集新增至應用程式  
  
-   將新的資料表加入至資料集  
  
-   資料行加入資料表  
  
-   設定資料表的主索引鍵  
  
## <a name="creating-a-new-windows-application"></a>建立新的 Windows 應用程式  
  
#### <a name="to-create-a-new-windows-application-project"></a>建立新的 Windows 應用程式專案  
  
1.  從**檔案** 功能表中，建立新的專案。  
  
2.  選擇程式設計語言**專案類型**窗格。  
  
3.  按一下  **Windows 應用程式**中**範本**窗格。  
  
4.  將專案命名為`DataTableWalkthrough`，然後按一下 **[確定]**。  
  
     Visual Studio 將專案加入**方案總管**，並顯示**Form1**設計工具中。  
  
## <a name="adding-a-new-dataset-to-the-application"></a>將新的資料集新增至應用程式  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>將新的資料集項目加入至專案  
  
1.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
     加入新項目 對話方塊隨即出現。  
  
2.  在 **範本**方塊中，選取**DataSet**。  
  
3.  按一下 [加入] 。  
  
     Visual Studio 會加入名為的檔案**DataSet1.xsd**專案中開啟它並**Dataset 設計工具**。  
  
## <a name="adding-a-new-datatable-to-the-dataset"></a>將新的 DataTable 加入至資料集  
  
#### <a name="to-add-a-new-data-table-to-the-dataset"></a>若要將新的資料表加入至資料集  
  
1.  拖曳**DataTable**從**資料集**索引標籤**工具箱**拖曳至**Dataset 設計工具**。  
  
     一個名為資料表**DataTable1**加入資料集。  
  
    > [!NOTE]
    >  若要建立資料表，其中包含 TableAdapter，請參閱[逐步解說： 以多個查詢建立 TableAdapter](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)。  
  
2.  按一下標題列**DataTable1**並將它重新命名`Music`。  
  
## <a name="adding-columns-to-the-data-table"></a>資料行加入資料表  
  
#### <a name="to-add-columns-to-the-data-table"></a>若要將資料行加入資料表  
  
1.  以滑鼠右鍵按一下**音樂**資料表。 指向**新增**，然後按一下**資料行**。  
  
2.  命名的資料行`SongID`。  
  
3.  在 **屬性**視窗中，將<xref:System.Data.DataColumn.DataType%2A>屬性設<xref:System.Int16?displayProperty=fullName>。  
  
4.  重複此程序，並新增下列資料行：  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>設定資料表的主索引鍵  
 所有資料的資料表應該都有主索引鍵。 主索引鍵可唯一識別資料表中的特定記錄。  
  
#### <a name="to-set-the-primary-key-of-the-data-table"></a>若要設定資料表的主索引鍵  
  
-   以滑鼠右鍵按一下**SongID**資料行，然後再按一下**設定主索引鍵**。  
  
     索引鍵圖示旁會出現**SongID**資料行。  
  
## <a name="saving-your-project"></a>儲存您的專案  
  
#### <a name="to-save-the-datatablewalkthrough-project"></a>若要儲存 DataTableWalkthrough 專案  
  
-   在 **檔案**功能表上，按一下**全部儲存**。  
  
## <a name="next-steps"></a>後續步驟  
 既然您已建立資料表，您可能想要執行下列動作之一：  
  
|以|請參閱|  
|--------|---------|  
|建立表單，以輸入資料|[逐步解說： 顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)。|  
|將資料加入至資料表|[將資料加入至 DataTable](http://msdn.microsoft.com/library/d6aa8474-7bde-48f7-949d-20dc38a1625b)。|  
|資料表中的檢視資料|[在 DataTable 中檢視資料](http://msdn.microsoft.com/library/1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc)。|  
|編輯資料|[DataTable 編輯](http://msdn.microsoft.com/library/f08008a9-042e-4de9-94f3-4f0e502b1eb5)|  
|從資料表刪除資料列|[刪除 DataRow](http://msdn.microsoft.com/library/c34f531d-4b9b-4071-b2d7-342c402aa586)|  
  
## <a name="see-also"></a>另請參閱  
 [連接到 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [將資料擷取至您的應用程式](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [儲存資料](../data-tools/saving-data.md)   
 [資料逐步解說](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)