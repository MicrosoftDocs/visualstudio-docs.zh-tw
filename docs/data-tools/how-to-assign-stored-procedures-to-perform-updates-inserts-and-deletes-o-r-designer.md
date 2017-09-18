---
title: "HOW TO：指派預存程序來執行更新、插入和刪除 (O/R 設計工具) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HOW TO：指派預存程序來執行更新、插入和刪除 (O/R 設計工具)
預存程序 \(Stored Procedure\) 可以加入至 O\/R 設計工具，而且可以當成一般 <xref:System.Data.Linq.DataContext> 方法來執行。預存程序也可以用來覆寫當儲存實體類別的變更至資料庫時 \(例如，呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 方法時\)，用於執行插入、更新和刪除作業的預設 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 執行階段行為。  
  
> [!NOTE]
>  如果預存程序傳回的值需要送回給用戶端 \(例如，在預存程序中計算的值\)，請在預存程序中建立輸出參數。如果您無法使用輸出參數，請撰寫部分方法實作 \(Implementation\)，而不要依賴 O\/R 設計工具產生的覆寫作業。與資料庫產生的值對應的成員，必須在 INSERT 或 UPDATE 作業成功完成之後設定為適當值。如需詳細資訊，請參閱[開發人員覆寫預設行為的責任](../Topic/Responsibilities%20of%20the%20Developer%20In%20Overriding%20Default%20Behavior.md)。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 會自動針對識別 \(自動遞增\)、rowguidcol \(資料庫產生的 GUID\) 和時間戳記資料行處理資料庫產生的值。其他資料行型別的資料庫產生值將非預期地產生 null 值。若要傳回資料庫產生的值，您應該手動將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 設定為 `true`，並將 <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> 設定為下列其中一項：<xref:System.Data.Linq.Mapping.AutoSync>、<xref:System.Data.Linq.Mapping.AutoSync> 或 <xref:System.Data.Linq.Mapping.AutoSync>。  
  
## 設定實體類別的更新行為  
 利用 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 實體類別中的資料變更來更新資料庫 \(插入、更新和刪除\) 的邏輯，預設是由 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 執行階段所提供。執行階段會根據資料表的結構描述 \(資料行和主索引鍵資訊\)，建立預設的 Insert、Update 和 Delete 命令。如果不想要使用這個預設行為，則可以指派特定的預存程序來執行管理資料表資料所需的插入、更新和刪除作業，即可設定更新行為。您也可以在沒有產生預設行為的情況下這麼做，例如實體類別對應至檢視時。最後，在資料庫需要透過預存程序進行資料表存取時，也可以覆寫預設更新行為。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 若要指派預存程序以覆寫實體類別的預設行為  
  
1.  在設計工具中開啟 \[**LINQ to SQL**\] 檔案 \(按兩下 \[**方案總管**\] 中的 .dbml 檔案\)。  
  
2.  展開 \[**伺服器總管**\]\/\[**資料庫總管**\] 中的 \[**預存程序**\]，尋找想要當成實體類別之 Insert、Update 和 \(或\) Delete 命令使用的預存程序。  
  
3.  將預存程序拖曳至 O\/R 設計工具。  
  
     預存程序會加入至方法窗格做為 <xref:System.Data.Linq.DataContext> 方法。如需詳細資訊，請參閱 [DataContext 方法 \(O\/R 設計工具\)](../data-tools/datacontext-methods-o-r-designer.md)。  
  
4.  選取想要使用預存程序執行更新的實體類別。  
  
5.  在 \[**屬性**\] 視窗中，選取要覆寫的命令 \(**Insert**、**Update** 或 **Delete**\)。  
  
6.  按一下 \[**使用執行階段**\] 字組旁邊的省略符號 \(...\)，以開啟 \[**設定行為**\] 對話方塊。  
  
7.  選取 \[**自訂**\]。  
  
8.  在 \[**自訂**\] 清單中，選取所要的預存程序。  
  
9. 檢查 \[**方法引數**\] 和 \[**類別屬性**\] 清單，以確認 \[**方法引數**\] 對應至適當的 \[**類別屬性**\]。請針對 Update 和 Delete 命令，將原始方法引數 \(*ArgumentName*\) 對應至原始屬性 \(*PropertyName* \(Original\)\)。  
  
    > [!NOTE]
    >  根據預設，方法引數會對應至同名的類別屬性。如果屬性名稱變更，使得資料表與實體類別之間不再對應，則您可能需要選取當 O\/R 設計工具無法判斷正確的對應時，所要對應的對等類別屬性。  
  
10. 按一下 \[**確定**\] 或 \[**套用**\]。  
  
    > [!NOTE]
    >  完成每一項變更後按一下 \[**套用**\]，即可繼續設定每個類別\/行為組合的行為。如果您在按一下 \[**套用**\] 之前變更了類別或行為，則會出現警告對話方塊，讓您可以套用任何變更。  
  
     若要還原成使用預設執行階段邏輯來進行更新，請在 \[**屬性**\] 視窗中按一下 Insert、Update 或 Delete 命令旁邊的省略符號，然後選取 \[**設定行為**\] 對話方塊中的 \[**使用執行階段**\]。  
  
## 請參閱  
 [物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext 方法 \(O\/R 設計工具\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [逐步解說：建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [逐步解說：建立 Northwind Customers 資料表的更新預存程序](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [插入、更新和刪除作業](../Topic/Insert,%20Update,%20and%20Delete%20Operations.md)