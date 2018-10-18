---
title: 填入 dataset 時關閉條件約束 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c47d3cb5e02117cb75ab86579b0cb3b166bd510
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259905"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>填入資料集時關閉條件約束
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
如果資料集包含條件約束 （例如外部索引鍵條件約束），theycan 就會引發對資料集執行的作業順序與相關的錯誤。 比方說，載入之前 loadingrelated 父資料錄的子記錄可以違反條件約束和導致錯誤。 當您載入子記錄時，條件約束檢查有相關的父記錄，因而引發錯誤。  
  
 如果沒有任何機制來允許暫時性條件約束的暫止，每次您嘗試載入的子資料表中的記錄，就會引發錯誤。 若要暫停資料集內的所有條件約束的另一個方法是使用<xref:System.Data.DataRow.BeginEdit%2A>，和<xref:System.Data.DataRow.EndEdit%2A>屬性。  
  
> [!NOTE]
>  驗證事件 (例如<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.RowChanging>) 將不會引發條件約束已關閉時。  
  
### <a name="to-suspend-update-constraints-programmatically"></a>若要以程式設計方式暫停更新條件約束  
  
-   下列範例示範如何暫時關閉條件約束檢查的資料集：  
  
     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>若要暫停使用 Dataset 設計工具的更新條件約束  
  
1.  開啟您的資料集，在[建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)。 如需詳細資訊，請參閱 <<c0> [ 如何： 以 Dataset 設計工具中開啟資料集](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。  
  
2.  在 [屬性]  視窗中，將 <xref:System.Data.DataSet.EnforceConstraints%2A> 屬性設定為 `false`。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Tableadapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [資料集中的關聯性](../data-tools/relationships-in-datasets.md)

