---
title: 填入 dataset 時關閉條件約束
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
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 40e19e7595c91429a8c52ddcdd01808a84197cc4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>填入 dataset 時關閉條件約束

如果資料集包含條件約束 （例如外部索引鍵條件約束），它們可以引發順序對資料集執行的作業相關的錯誤。 例如，載入之前載入的子記錄相關的父資料錄可能違反條件約束，而且會導致錯誤。 您載入子記錄，如條件約束檢查有相關的父記錄，並引發錯誤。

如果沒有任何機制，讓暫止的暫時的條件約束，每次您嘗試載入子資料表中的記錄，就會引發錯誤。 若要暫停資料集內的所有條件約束的另一個方法是使用<xref:System.Data.DataRow.BeginEdit%2A>，和<xref:System.Data.DataRow.EndEdit%2A>屬性。

> [!NOTE]
> 驗證事件 (例如，<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.RowChanging>) 時，系統不會引發條件約束均已關閉。

## <a name="to-suspend-update-constraints-programmatically"></a>若要以程式設計方式暫止更新條件約束

-   下列範例會示範如何暫時關閉條件約束檢查的資料集：

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>若要暫停使用 Dataset 設計工具的更新條件約束

1.  開啟您的資料集在**Dataset 設計工具**。 如需詳細資訊，請參閱[逐步解說： 在 Dataset 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。

2.  在**屬性**視窗中，將<xref:System.Data.DataSet.EnforceConstraints%2A>屬性`false`。

## <a name="see-also"></a>另請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)
- [資料集中的關聯性](../data-tools/relationships-in-datasets.md)