---
title: "逐步解說：以 DataSet 設計工具建立 DataTable | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "資料 [Visual Studio], DataSet 設計工具"
  - "DataSet 設計工具, 建立資料表"
  - "DataTable 物件, 建立"
  - "資料表 [Visual Studio], 建立"
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 逐步解說：以 DataSet 設計工具建立 DataTable
這個逐步解說將說明如何使用 \[**DataSet 設計工具**\] 建立 <xref:System.Data.DataTable> \(不含 TableAdapter\)。  如需建立包含 TableAdapter 的資料表的詳細資訊，請參閱 [如何：建立 TableAdapter](../data-tools/create-and-configure-tableadapters.md)。  
  
 逐步解說將說明的工作包括：  
  
-   建立新的 Windows 應用程式專案  
  
-   將新資料集加入應用程式  
  
-   將新的資料表加入資料集  
  
-   將資料行加入資料表  
  
-   設定資料表的主索引鍵  
  
## 建立新的 Windows 應用程式  
  
#### 若要建立新的 Windows 應用程式專案  
  
1.  從 \[**檔案**\] 功能表中，建立新專案。  
  
2.  在 \[**專案類型**\] 窗格中，選擇程式設計語言。  
  
3.  在 \[**範本**\] 窗格中，按一下 \[**Windows 應用程式**\]。  
  
4.  將專案命名為 `DataTableWalkthrough`，再按 \[**確定**\]。  
  
     Visual Studio 隨即將專案加入至 \[**方案總管**\]，並在設計工具中顯示 \[**Form1**\]。  
  
## 將新資料集加入應用程式  
  
#### 若要將新的資料集項目加入專案  
  
1.  在 \[**專案**\] 功能表上，按一下 \[**加入新項目**\]。  
  
     \[加入新項目\] 對話方塊隨即出現。  
  
2.  在 \[**範本**\] 方塊中選取 \[**資料集**\]。  
  
3.  按一下 \[**加入**\]。  
  
     Visual Studio 隨即將名為 **DataSet1.xsd** 的檔案加入至專案，並且在 \[**DataSet 設計工具**\] 中開啟它。  
  
## 將新的 DataTable 加入資料集  
  
#### 若要將新的資料表加入資料集  
  
1.  從 \[**工具箱**\] 的 \[**資料集**\] 索引標籤，將 \[**DataTable**\] 拖曳至 \[**DataSet 設計工具**\]。  
  
     名為 **DataTable1** 的資料表隨即加入至資料集。  
  
    > [!NOTE]
    >  若要建立包含 TableAdapter 的資料表，請參閱[逐步解說：以多個查詢建立 TableAdapter](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)。  
  
2.  按一下 \[**DataTable1**\] 的標題列，將它重新命名為 `Music`。  
  
## 將資料行加入資料表  
  
#### 若要將資料行加入資料表  
  
1.  在 \[**Music**\] 資料表上按一下滑鼠右鍵。  指向 \[**加入**\]，再按 \[**資料行**\]。  
  
2.  將資料行命名為 `SongID`。  
  
3.  在 \[**屬性**\] 視窗中，將 <xref:System.Data.DataColumn.DataType%2A> 屬性設定為 <xref:System.Int16?displayProperty=fullName>。  
  
4.  重複這個程序，加入下列資料行：  
  
     `SongTitle`：<xref:System.String?displayProperty=fullName>  
  
     `Artist`：<xref:System.String?displayProperty=fullName>  
  
     `Genre`：<xref:System.String?displayProperty=fullName>  
  
## 設定資料表的主索引鍵  
 所有資料表都應該擁有主索引鍵。  只有主索引鍵能夠識別資料表中的特定資料錄。  
  
#### 若要設定資料表的主索引鍵  
  
-   在 \[**SongID**\] 資料行上按一下滑鼠右鍵，再按 \[**設定主索引鍵**\]。  
  
     \[**SongID**\] 資料行旁邊就會出現鑰匙圖示。  
  
## 儲存專案  
  
#### 若要儲存 DataTableWalkthrough 專案  
  
-   在 \[**檔案**\] 功能表上，按一下 \[**全部儲存**\]。  
  
## 後續步驟  
 現在您已建立資料表，可執行下列其中一個動作：  
  
|若要|請參閱|  
|--------|---------|  
|建立表單以輸入資料|[逐步解說：顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|將資料加入資料表|[將資料加入至 DataTable](../Topic/Adding%20Data%20to%20a%20DataTable.md).|  
|檢視資料表中的資料|[檢視 DataTable 中的資料](../Topic/Viewing%20Data%20in%20a%20DataTable.md).|  
|編輯資料|[DataTable 編輯](../Topic/DataTable%20Edits.md)|  
|將資料列從資料表中刪除|[DataRow 刪除](../Topic/DataRow%20Deletion.md)|  
  
## 請參閱  
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)   
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)