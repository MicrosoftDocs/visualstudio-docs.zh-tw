---
title: 填入資料集時關閉條件約束
description: 瞭解如何在填滿資料集時關閉條件約束。 以程式設計方式或使用 DataSet 設計工具暫止 update 條件約束。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 3280894ba1634f9775def74a88dcb413c94ba77a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215704"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>填入資料集時關閉條件約束

如果資料集包含 (之類的條件約束，例如外鍵條件約束) ，它們可能會引發與針對資料集執行之作業順序相關的錯誤。 例如，載入相關的父記錄之前載入子記錄可能會違反條件約束，並導致錯誤。 一旦載入子記錄，條件約束就會檢查相關的父記錄，並引發錯誤。

如果沒有允許暫時條件約束暫止的機制，每次您嘗試將記錄載入子資料工作表時，都會引發錯誤。 另一個暫停資料集中之條件約束的方法是使用 <xref:System.Data.DataRow.BeginEdit%2A> 、和 <xref:System.Data.DataRow.EndEdit%2A> 屬性。

> [!NOTE]
> 例如， <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> 在關閉條件約束時，將不會引發 (的驗證事件和) 。

## <a name="to-suspend-update-constraints-programmatically"></a>以程式設計方式暫停 update 條件約束

- 下列範例顯示如何在資料集中暫時關閉條件約束檢查：

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet10":::

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>使用 DataSet 設計工具暫止更新條件約束

1. 在 [DataSet 設計工具] 中開啟資料集。 如需詳細資訊，請參閱 [逐步解說：在 DataSet 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。

2. 在 [屬性]  視窗中，將 <xref:System.Data.DataSet.EnforceConstraints%2A> 屬性設定為 `false`。

## <a name="see-also"></a>另請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)
- [資料集中的關聯性](../data-tools/relationships-in-datasets.md)
