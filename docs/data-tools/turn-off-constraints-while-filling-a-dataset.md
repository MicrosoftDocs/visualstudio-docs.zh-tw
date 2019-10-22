---
title: 填入資料集時關閉條件約束
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b8ab7bb827c478360a64d65f44af6770c77ebf77
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648127"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>填入資料集時關閉條件約束

如果資料集包含條件約束（例如外鍵條件約束），它們可能會引發與針對資料集執行之作業順序相關的錯誤。 例如，載入相關的父記錄之前載入子記錄可能會違反條件約束，並造成錯誤。 一旦您載入子記錄，條件約束就會檢查相關的父記錄，並引發錯誤。

如果沒有機制允許暫時條件約束暫止，則每次您嘗試將記錄載入子資料工作表時，就會引發錯誤。 另一個暫停 dataset 中所有條件約束的方法是使用 <xref:System.Data.DataRow.BeginEdit%2A>，並 <xref:System.Data.DataRow.EndEdit%2A> 屬性。

> [!NOTE]
> 關閉條件約束時，不會引發驗證事件（例如，<xref:System.Data.DataTable.ColumnChanging> 和 <xref:System.Data.DataTable.RowChanging>）。

## <a name="to-suspend-update-constraints-programmatically"></a>以程式設計方式暫止更新條件約束

- 下列範例顯示如何暫時關閉資料集中的條件約束檢查：

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>若要使用 DataSet 設計工具暫停更新條件約束

1. 在 [DataSet 設計工具] 中開啟資料集。 如需詳細資訊，請參閱[逐步解說：在 DataSet 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。

2. 在 [屬性] 視窗中，將 <xref:System.Data.DataSet.EnforceConstraints%2A> 屬性設定為 `false`。

## <a name="see-also"></a>請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)
- [資料集中的關聯性](../data-tools/relationships-in-datasets.md)