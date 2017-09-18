---
title: "如何：從物件中將資料儲存至資料庫 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "資料 [Visual Studio], 儲存"
  - "資料存取 [Visual Studio], 物件"
  - "儲存資料"
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 9
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：從物件中將資料儲存至資料庫
您可以將物件的資料儲存至資料庫中，方法是將物件的值傳遞至其中一個 TableAdapter 的 DBDirect 方法 \(例如 `TableAdapter.Insert`\)。  如需詳細資訊，請參閱 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)。  
  
 若要儲存物件集合的資料，請在物件的集合中執行迴圈 \(Loop\) \(例如，for\-next 迴圈\)，然後使用其中一個 TableAdapter 的 DBDirect 方法，將每個物件的值傳送至資料庫中。  
  
 根據預設，DBDirect 方法是在 TableAdapter 上建立的，而且這些方法可直接對資料庫執行。  您可以直接呼叫這些方法，而不需要 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 物件來調整變更，以便將更新傳送至資料庫。  
  
> [!NOTE]
>  當您在設定 TableAdapter 時，主查詢必須提供足夠的資訊，才會建立 DBDirect 方法。  例如，如果 TableAdapter 設定為從並未定義主索引鍵資料行的資料表查詢資料時，它就不會產生 DBDirect 方法。  
  
|TableAdapter DBDirect 方法|描述|  
|------------------------------|--------|  
|`TableAdapter.Insert`|將新資料錄加入至資料庫，並讓您傳入個別的資料行值做為方法參數。|  
|`TableAdapter.Update`|更新資料庫中的現有資料錄。  此 `Update` 方法會採用原始和新的資料行值做為方法參數。  原始值是用來找出原始資料錄，而新值則是用來更新該資料錄。<br /><br /> 此外，`TableAdapter.Update` 方法也會用來將資料集的變更調整回資料庫中，方式是採用 <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow> 或 <xref:System.Data.DataRow> 的陣列做為方法參數。|  
|`TableAdapter.Delete`|根據傳入做為方法參數的原始資料行值，從資料庫刪除現有的資料錄。|  
  
### 若要將物件的新資料錄儲存至資料庫中  
  
-   將值傳遞至 `TableAdapter.Insert` 方法，藉以建立資料錄。  
  
     下列範例會在 `Customers` 資料表中建立新的客戶資料錄，方法是將 `currentCustomer` 物件中的值傳遞至 `TableAdapter.Insert` 方法。  
  
     [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]  
  
### 若要將物件的現有資料錄更新至資料庫中  
  
-   修改資料錄，方法是呼叫 `TableAdapter.Update` 方法、傳入新值以更新資料錄，並傳入原始值以找出資料錄。  
  
    > [!NOTE]
    >  您的物件必須維護原始值，才能將它們傳遞至 `Update` 方法。  這個範例會使用含有 `orig` 前置詞的屬性，儲存原始值。  
  
     下列範例會在 `Customers` 資料表中更新現有的資料錄，方法是將 `Customer` 物件中的新和原始值傳遞至 `TableAdapter.Update` 方法。  
  
     [!code-cs[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]  
  
### 若要從資料庫刪除現有的資料錄  
  
-   刪除資料錄，方法是呼叫 `TableAdapter.Delete` 方法，並傳入原始值以找出資料錄。  
  
    > [!NOTE]
    >  您的物件必須維護原始值，才能將它們傳遞至 `Delete` 方法。  這個範例會使用含有 `orig` 前置詞的屬性，儲存原始值。  
  
     下列範例會從 `Customers` 資料表刪除資料錄，方法是將 `Customer` 物件中的原始值傳遞至 `TableAdapter.Delete` 方法。  
  
     [!code-cs[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]  
  
## .NET Framework 安全性  
 您必須擁有在資料庫的資料表上執行選取 INSERT、UPDATE 或 DELETE 的使用權限。  
  
## 請參閱  
 [Visual Studio 中的物件繫結](../data-tools/bind-objects-in-visual-studio.md)   
 [如何：連接至物件中的資料](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)   
 [逐步解說：連接至物件中的資料 \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)   
 [如何：以 TableAdapter 直接存取資料庫](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)