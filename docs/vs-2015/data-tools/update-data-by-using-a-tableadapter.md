---
title: 使用 TableAdapter 更新資料 |Microsoft Docs
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
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ec53e42a5e49d48e76c6c00e2ffbd5a8a3daafa0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943473"
---
# <a name="update-data-by-using-a-tableadapter"></a>使用 TableAdapter 更新資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
在資料集中的資料已修改且驗證之後，您可以將更新的資料傳送回 databaseby 呼叫`Update`TableAdapter 的方法。 `Update`方法會更新單一資料表，並執行正確的命令 （INSERT、 UPDATE 或 DELETE） 根據<xref:System.Data.DataRow.RowState%2A>的資料表中每個資料列。 當資料集有相關的資料表時，則 Visual Studio 會產生 TableAdapterManager 類別，您用來進行更新。 TableAdapterManager 類別可確保以正確的順序，根據資料庫所定義的外部索引鍵條件約束會進行更新。 當您使用資料繫結控制項時，資料繫結架構會建立呼叫 tableAdapterManager TableAdapterManager 類別成員變數。 如需詳細資訊，請參閱 <<c0> [ 階層式更新概觀](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)。  
  
> [!NOTE]
>  當您嘗試更新資料來源的資料集的內容時，您可能會收到錯誤。若要避免錯誤，我們建議說明將會呼叫配接器的程式碼`Update`方法內`try` / `catch`區塊。  
  
 更新資料來源的確切程序會根據商務需求而有所不同，但包含下列步驟：  
  
1.  呼叫的介面卡`Update`方法中的`try` / `catch`區塊。  
  
2.  如果攔截到例外狀況時，找出造成錯誤的資料列。 如需詳細資訊，請參閱[如何：找出有錯誤的資料列](http://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c)。  
  
3.  調解這個問題，資料中的資料列 （如果可以，以程式設計方式或出示無效的資料列已修改的使用者），並再試一次更新 (<xref:System.Data.DataRow.HasErrors%2A>， <xref:System.Data.DataTable.GetErrors%2A>)。  
  
## <a name="savedata-to-a-database"></a>Savedata 至資料庫  
 呼叫`Update`TableAdapter 的方法。 傳遞包含要寫入至資料庫值的資料表的名稱。  
  
#### <a name="to-update-a-database-by-using-a-tableadapter"></a>使用 TableAdapter 更新資料庫  
  
-   括住的 TableAdapter`Update`方法中的`try` / `catch`區塊。 下列範例示範如何更新的內容`Customers`資料表中`NorthwindDataSet`內在`try` / `catch`區塊。  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
## <a name="see-also"></a>另請參閱  
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
