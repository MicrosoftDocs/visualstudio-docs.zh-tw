---
title: 如何： 認可資料集中的變更 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataSet.AcceptChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], committing changes
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 41d27c248763f42db6543db0a9b4e56e4c4eac82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276428"
---
# <a name="how-to-commit-changes-in-a-dataset"></a>如何：認可資料集中的變更
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您在資料集中的記錄中進行變更，藉由更新、 插入和刪除記錄，資料集就會維護資料錄的原始和目前的版本。 此外，每個資料列的<xref:System.Data.DataRow.RowState%2A>是否記錄位於其原始狀態或已更新、 插入或刪除記錄的屬性。 當您需要尋找特定版本的資料列，則此資訊會非常有用。 一般而言，您會取得所有已變更的記錄傳送到另一個處理序的子集。 如需詳細資訊，請參閱 <<c0> [ 如何： 擷取變更資料列](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)。 在處理所有變更的資料列之後，您可以藉由呼叫認可所做的變更`AcceptChanges`方法<xref:System.Data.DataSet>， <xref:System.Data.DataTable>，或<xref:System.Data.DataRow>。 `AcceptChanges`呼叫的 update 方法時，會自動呼叫 「 方法[TableAdapter](../data-tools/tableadapter-overview.md)或資料配接器。 呼叫`AcceptChanges`之後將變更提交至資料庫。  
  
 當您呼叫<xref:System.Data.DataSet.AcceptChanges%2A>上<xref:System.Data.DataSet>，任何<xref:System.Data.DataRow>仍處於編輯模式的物件已成功結束其編輯。 <xref:System.Data.DataRow.RowState%2A>每個屬性<xref:System.Data.DataRow>也會變更;<xref:System.Data.DataRowState>並<xref:System.Data.DataRowState>資料列會變成<xref:System.Data.DataRowState>，和<xref:System.Data.DataRowState>移除的資料列。  
  
 如果<xref:System.Data.DataSet>包含<xref:System.Data.ForeignKeyConstraint>物件，叫用<xref:System.Data.DataSet.AcceptChanges%2A>方法也會導致<xref:System.Data.AcceptRejectRule>強制執行。  
  
### <a name="to-commit-changes-in-a-dataset"></a>若要認可的資料集內的變更  
  
-   呼叫`AcceptChanges`上的方法<xref:System.Data.DataSet>， <xref:System.Data.DataTable>，或<xref:System.Data.DataRow>認可這些物件中的變更。  
  
     下列範例示範如何呼叫`AcceptChanges`方法來認可變更`Customers`之後更新資料來源的資料表：  
  
     [!code-csharp[VbRaddataEditing#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#11)]
     [!code-vb[VbRaddataEditing#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#11)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [儲存資料](../data-tools/saving-data.md)   
 [如何： 擷取已變更的資料列](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)