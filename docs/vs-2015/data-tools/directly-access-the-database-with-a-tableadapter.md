---
title: 直接存取資料庫以 tableadapter |Microsoft Docs
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
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5226f5c235b3af10fba4fd0fab3ee44ceb72a93e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654096"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>以 TableAdapter 直接存取資料庫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

除了`InsertCommand`， `UpdateCommand`，和`DeleteCommand`，可以直接對資料庫執行的方法以建立 TableAdapters。 這些方法 (`TableAdapter.Insert`， `TableAdapter.Update`，和`TableAdapter.Delete`) 可以呼叫來操作直接在資料庫中的資料。  
  
 如果您不想要建立這些直接方法，設定 TableAdapter`GenerateDbDirectMethods`屬性，以`false`中**屬性**視窗。 如果除了 TableAdapter 的主要查詢的 TableAdapter 加入任何查詢，都不會產生這些 DbDirect 方法的獨立查詢。  
  
## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly 至資料庫  
 呼叫 TableAdapter 的 DbDirect 方法可執行您嘗試完成的工作。  
  
#### <a name="to-insert-new-records-directly-into-a-database"></a>若要直接將新記錄插入資料庫  
  
-   呼叫 TableAdapter 的`Insert`方法，傳遞每個資料行做為參數的值。 下列程序使用`Region`Northwind databaseas 資料表範例。  
  
    > [!NOTE]
    >  如果您沒有可用的執行個體，具現化您想要使用的 TableAdapter。  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
#### <a name="to-update-records-directly-in-a-database"></a>若要更新直接在資料庫中的記錄  
  
-   呼叫 TableAdapter 的`Update`方法並傳入新值和原始值的每個資料行做為參數。  
  
    > [!NOTE]
    >  如果您沒有可用的執行個體，具現化您想要使用的 TableAdapter。  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
#### <a name="to-delete-records-directly-from-a-database"></a>若要直接從資料庫刪除記錄  
  
-   呼叫 TableAdapter`Delete`方法，傳遞每個資料行做為參數的值`Delete`方法。 下列程序使用`Region`Northwind databaseas 資料表範例。  
  
    > [!NOTE]
    >  如果您沒有可用的執行個體，具現化您想要使用的 TableAdapter。  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>另請參閱  
 [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)
