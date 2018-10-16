---
title: 逐步解說： 連接至本機資料庫檔案 (Windows Form) 中的資料 |Microsoft Docs
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
- databases, connecting to
- local data, SQL Express
- SQL Express, walkthroughs
- SQL Express, connecting
- data [Visual Studio], local
- data [Visual Studio], connecting to SQL Express
ms.assetid: 5e16b7da-3fdc-4e69-bdb4-e8e700481811
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 71898c88a8d7a1d4a119a7e7a932e295ae12eb34
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176159"
---
# <a name="walkthrough-connecting-to-data-in-a-local-database-file-windows-forms"></a>逐步解說：連接至本機資料庫檔案中的資料 (Windows Form)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以藉由建立資料集，然後將資料繫結控制項加入至應用程式的方式，快速輕鬆地在應用程式中顯示本機資料庫檔案的資料。 在本逐步解說中，您將會顯示從您依照中的步驟建立的本機資料庫檔案的資料[使用設計工具建立 SQL database](../data-tools/create-a-sql-database-by-using-a-designer.md)。 在您建立 Windows Form 專案後，您將連接至該資料庫，並指定要讓 Customers 資料表的資料出現在應用程式表單的資料格中。  
  
 當您在 Visual Studio 2013 中建立資料庫時，會使用 SQL Server Express LocalDB 引擎來存取 SQL Server 2012 中的資料庫檔案 (.mdf)。 在舊版 Visual Studio 中，會使用 SQL Server Express 引擎存取資料庫檔案 (.mdf)。 請參閱[本機資料概觀](../data-tools/local-data-overview.md)。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
 本逐步解說包含下列工作：  
  
-   [建立和設定資料集](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_CreateDataset)  
  
-   [加入資料繫結控制項](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_AddCtrls)  
  
## <a name="prerequisites"></a>必要條件  
 若要完成此逐步解說中，您需要存取 SampleDatabase.mdf 資料庫所建立的完成[使用設計工具建立 SQL database](../data-tools/create-a-sql-database-by-using-a-designer.md)。  
  
##  <a name="BKMK_CreateDataset"></a> 建立和設定資料集  
  
#### <a name="to-create-and-configure-a-dataset"></a>若要建立及設定資料集  
  
1.  建立 Windows Forms 專案，並將它命名**為 ConnectLocalData**。  
  
     請參閱[用戶端應用程式](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)。  
  
2.  如果**資料來源**視窗未顯示、 選擇 Shift Alt D 鍵或在功能表列上選擇 **檢視**，**其他 Windows**，**顯示資料來源**.  
  
3.  在 [**資料來源**] 視窗中，選擇**加入新的資料來源**連結。  
  
     在 [**資料來源組態精靈**，選擇**下一步]** 按鈕兩次接受預設設定。  
  
4.  在 [**選擇資料連接**頁面上，選擇**新的連接**] 按鈕。  
  
     **選擇資料來源** 對話方塊隨即出現。  
  
5.  在 [**資料來源**清單中，選擇**Microsoft SQL Server 資料庫檔案**，然後選擇**繼續**] 按鈕。  
  
     **加入連接** 對話方塊隨即出現。  
  
6.  在 **資料庫檔名**方塊中，指定您完成建立的檔案[使用設計工具建立 SQL database](../data-tools/create-a-sql-database-by-using-a-designer.md)，或選擇**瀏覽**按鈕，然後尋找該檔案。  
  
     根據預設，檔案位於使用者\\*YourAccount*\Documents\Visual Studio*版本*\Projects\SampleDatabaseWalkthrough\SampleDatabaseWalkthrough。  
  
7.  底下**登入伺服器**，接受預設值，然後選擇**確定**按鈕，然後再選擇**下一步**  按鈕。  
  
    > [!NOTE]
    >  當您連接至本機資料庫檔案時，可以在專案中建立資料庫的複本，或是連接至目前位置上的資料庫檔案。 請參閱[如何： 管理專案中的本機資料檔](../data-tools/how-to-manage-local-data-files-in-your-project.md)。  
  
8.  在出現的對話方塊中，選擇**是**將資料庫檔案複製到您的專案。  
  
9. 在 **儲存連接字串儲存到應用程式組態檔**頁面上，選擇**下一步**  按鈕。  
  
10. 上**選擇您的資料庫物件**頁面上，展開**資料表**節點中，選取**客戶**並**訂單**核取方塊，然後選擇**完成** 按鈕。  
  
     **SampleDatabaseDataSet**新增至您的專案，而**客戶**並**訂單**資料表會出現在**資料來源**視窗。  
  
##  <a name="BKMK_AddCtrls"></a> 加入資料繫結控制項  
  
#### <a name="to-add-data-bound-controls"></a>若要加入資料繫結控制項  
  
1.  移動主**客戶**從節點**Zdroje dat**  視窗拖曳到**Form1**。  
  
     <xref:System.Windows.Forms.DataGridView> 以及用於巡覽資料錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 會出現在表單上。 A [SampleDatabaseDataSet](../data-tools/dataset-tools-in-visual-studio.md)， [CustomersTableAdapter](../data-tools/tableadapter-overview.md)， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>會出現在元件匣。  
  
2.  若要執行應用程式並顯示您在先前逐步解說中加入的資料，請選擇 F5 鍵。  
  
3.  選擇黃色加號圖示 (![在 Windows Form 中的 [新增] 按鈕](../data-tools/media/addrecord.png "AddRecord")) 中，加入客戶記錄，並儲存您的變更選擇磁碟圖示 (![Windows 表單中的[儲存]按鈕](../data-tools/media/saveinwf.png "SaveInWF"))。  
  
4.  刪除記錄，您剛建立選擇它，再選擇紅色刪除圖示 (![在 Windows Form 中的 [刪除] 按鈕](../data-tools/media/deleterecord.png "DeleteRecord"))。  
  
## <a name="next-steps"></a>後續步驟  
 您可以建立或修改資料集內的物件，如果您開啟中的資料來源[建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)。 您還可以將驗證邏輯加入資料集內資料表的 <xref:System.Data.DataTable.ColumnChanging> 或 <xref:System.Data.DataTable.RowChanging> 事件中。 請參閱[驗證資料集中](../data-tools/validate-data-in-datasets.md)。  
  
## <a name="see-also"></a>另請參閱  
 [本機資料概觀](../data-tools/local-data-overview.md)   
 [如何： 管理專案中的本機資料檔](../data-tools/how-to-manage-local-data-files-in-your-project.md)   
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [連接到 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [將資料擷取至您的應用程式](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [儲存資料](../data-tools/saving-data.md)