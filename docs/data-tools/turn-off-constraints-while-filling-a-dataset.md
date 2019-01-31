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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: b78bd412343888a5f90fdc84f1c4fe31a3babaa7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996762"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>填入資料集時關閉條件約束

如果資料集包含條件約束 （例如外部索引鍵條件約束），它們可以引發順序對資料集執行的作業相關的錯誤。 例如，載入之前載入的子記錄相關的父資料錄可能違反條件約束，而且會導致錯誤。 當您載入子記錄時，條件約束檢查有相關的父記錄，因而引發錯誤。

如果沒有任何機制來允許暫時性條件約束的暫止，每次您嘗試載入的子資料表中的記錄，就會引發錯誤。 若要暫停資料集內的所有條件約束的另一個方法是使用<xref:System.Data.DataRow.BeginEdit%2A>，和<xref:System.Data.DataRow.EndEdit%2A>屬性。

> [!NOTE]
> 驗證事件 (例如<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.RowChanging>) 將不會引發條件約束已關閉時。

## <a name="to-suspend-update-constraints-programmatically"></a>若要以程式設計方式暫停更新條件約束

-   下列範例示範如何暫時關閉條件約束檢查的資料集：

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>若要暫停使用 Dataset 設計工具的更新條件約束

1.  在 **DataSet 設計工具**中開啟資料集。 如需詳細資訊，請參閱[逐步解說：在 Dataset 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。

2.  在 [屬性]  視窗中，將 <xref:System.Data.DataSet.EnforceConstraints%2A> 屬性設定為 `false`。

## <a name="see-also"></a>另請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)
- [資料集中的關聯性](../data-tools/relationships-in-datasets.md)