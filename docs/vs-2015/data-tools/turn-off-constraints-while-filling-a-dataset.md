---
title: 填入資料集時關閉條件約束 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6646f669bf2c465d8e0f705f8fba956b979952ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667171"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>填入資料集時關閉條件約束
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果資料集包含條件約束（例如外鍵條件約束），theycan 會引發與針對資料集執行之作業順序相關的錯誤。 例如，在 loadingrelated 父記錄之前載入子記錄可能會違反條件約束並造成錯誤。 一旦您載入子記錄，條件約束就會檢查相關的父記錄，並引發錯誤。

 如果沒有機制允許暫時條件約束暫止，則每次您嘗試將記錄載入子資料工作表時，就會引發錯誤。 另一個暫停 dataset 中所有條件約束的方法是使用 <xref:System.Data.DataRow.BeginEdit%2A>，並 <xref:System.Data.DataRow.EndEdit%2A> 屬性。

> [!NOTE]
> 關閉條件約束時，不會引發驗證事件（例如，<xref:System.Data.DataTable.ColumnChanging> 和 <xref:System.Data.DataTable.RowChanging>）。

### <a name="to-suspend-update-constraints-programmatically"></a>以程式設計方式暫止更新條件約束

- 下列範例顯示如何暫時關閉資料集中的條件約束檢查：

     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]

### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>若要使用 DataSet 設計工具暫停更新條件約束

1. 在 DataSet 設計工具中開啟您的資料集。 如需詳細資訊，請參閱[如何：在 DataSet 設計工具中開啟資料集](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。

2. 在 [屬性] 視窗中，將 <xref:System.Data.DataSet.EnforceConstraints%2A> 屬性設定為 `false`。

## <a name="see-also"></a>請參閱
 使用[資料集中](../data-tools/relationships-in-datasets.md)[的 Tableadapter 關聯性填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)
