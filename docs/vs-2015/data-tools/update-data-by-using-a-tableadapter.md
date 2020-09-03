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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 312bf75100d2b9b270b45776c5f7ded21ab6ac52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72602339"
---
# <a name="update-data-by-using-a-tableadapter"></a>使用 TableAdapter 更新資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您資料集中的資料已修改並驗證之後，您可以將更新的資料傳送回 databaseby，呼叫 `Update` TableAdapter 的方法。 `Update`方法會更新單一資料表，並根據 <xref:System.Data.DataRow.RowState%2A> 資料表中每個資料列的，執行正確的命令 (插入、更新或刪除) 。 當資料集有相關的資料表時，Visual Studio 會產生您用來執行更新的 TableAdapterManager 類別。 TableAdapterManager 類別可確保根據資料庫中定義的外鍵條件約束，以正確的順序進行更新。 當您使用資料繫結控制項時，資料系結架構會建立名為 tableAdapterManager 之 TableAdapterManager 類別的成員變數。 如需詳細資訊，請參閱 [階層式更新總覽](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)。

> [!NOTE]
> 當您嘗試以資料集的內容更新資料來源時，可能會收到錯誤。若要避免錯誤，建議 thatyou 將呼叫介面卡方法的程式碼放在 `Update` `try` / `catch` 區塊內。

 更新資料來源的確切程式會根據商務需求而有所不同，但包含下列步驟：

1. 呼叫區塊中的介面卡 `Update` 方法 `try` / `catch` 。

2. 如果攔截到例外狀況，請找出造成錯誤的資料列。 如需詳細資訊，請參閱 [如何：找出有錯誤的資料列](https://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c)。

3. 如果可以的話，也可以透過程式設計的方式協調資料列中的問題 (，或向使用者呈現不正確資料列以進行修改) ，然後再試一次更新 (<xref:System.Data.DataRow.HasErrors%2A> ， <xref:System.Data.DataTable.GetErrors%2A>) 。

## <a name="savedata-to-a-database"></a>Savedata 至資料庫
 呼叫 `Update` TableAdapter 的方法。 傳遞包含要寫入資料庫之值的資料表名稱。

#### <a name="to-update-a-database-by-using-a-tableadapter"></a>使用 TableAdapter 更新資料庫

- 將 TableAdapter 的 `Update` 方法放在 `try` / `catch` 區塊中。 下列範例示範如何 `Customers` `NorthwindDataSet` 從區塊內更新中的資料表內容 `try` / `catch` 。

     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]

## <a name="see-also"></a>另請參閱
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
