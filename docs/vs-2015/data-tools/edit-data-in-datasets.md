---
title: 編輯資料集中的資料 |Microsoft Docs
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
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 699ee9b6e7a68c6a79f7f7dac526127206e8aa42
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672395"
---
# <a name="edit-data-in-datasets"></a>編輯資料集中的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

編輯資料表中的資料，就像您在任何資料庫中編輯資料表中的資料一樣。 此程式可以包含插入、更新和刪除資料表中的記錄。 在資料系結表單中，您可以指定哪些欄位可供使用者編輯。 在這些情況下，資料系結基礎結構會處理所有變更追蹤，以便稍後將變更傳送回資料庫。 如果您以程式設計方式對資料進行編輯，而且想要將這些變更傳回至資料庫，則必須使用為您執行變更追蹤的物件和方法。

 除了變更實際資料以外，您也可以查詢 <xref:System.Data.DataTable> 以傳回特定的資料列。 例如，您可以查詢個別的資料列、特定的資料列版本（原始和建議的資料列）、已變更的資料列，或有錯誤的資料列。

## <a name="to-edit-rows-in-a-dataset"></a>編輯資料集中的資料列
 若要編輯 <xref:System.Data.DataTable> 中的現有資料列，您必須找出您想要編輯的 <xref:System.Data.DataRow>，然後將更新的值指派給所需的資料行。

 如果您不知道您想要編輯之資料列的索引，請使用 `FindBy` 方法，依主要金鑰進行搜尋：

 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]

 如果您知道資料列索引，您可以存取和編輯資料列，如下所示：

 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]

## <a name="to-insert-new-rows-into-a-dataset"></a>若要將新的資料列插入 dataset
 使用資料繫結控制項的應用程式通常會透過[BindingNavigator 控制項](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e)上的 [**加入新**的] 按鈕來加入新的記錄。

 若要手動將新記錄加入至資料集，請在 DataTable 上呼叫方法來建立新的資料列。 然後將資料列新增至 <xref:System.Data.DataTable> 的 <xref:System.Data.DataRow> 集合（<xref:System.Data.DataTable.Rows%2A>）：

 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]

 為了保留資料集將更新傳送至資料來源所需的資訊，請使用 <xref:System.Data.DataRow.Delete%2A> 方法來移除資料表中的資料列。 例如，如果您的應用程式使用 TableAdapter （或 <xref:System.Data.Common.DataAdapter>），TableAdapter 的 `Update` 方法會刪除資料庫中具有 <xref:System.Data.DataRowState> <xref:System.Data.DataRow.RowState%2A> 的資料列。

 如果您的應用程式不需要將更新傳送回資料來源，則可以直接存取資料列集合（<xref:System.Data.DataRowCollection.Remove%2A>）來移除記錄。

#### <a name="to-delete-records-from-a-data-table"></a>若要從資料表中刪除記錄

- 呼叫 <xref:System.Data.DataRow> 的 <xref:System.Data.DataRow.Delete%2A> 方法。

     這個方法不會實際移除記錄。 相反地，它會標示要刪除的記錄。

    > [!NOTE]
    > 如果您取得 <xref:System.Data.DataRowCollection> 的 count 屬性，則產生的計數會包含已標示為要刪除的記錄。 若要取得未標示為要刪除之記錄的精確計數，您可以對集合進行迴圈查看每筆記錄的 <xref:System.Data.DataRow.RowState%2A> 屬性。 （標記為刪除的記錄具有 <xref:System.Data.DataRowState> 的 <xref:System.Data.DataRow.RowState%2A>。）或者，您也可以建立資料集的資料檢視，以便根據資料列狀態進行篩選，並從該處取得 count 屬性。

     下列範例顯示如何呼叫 <xref:System.Data.DataRow.Delete%2A> 方法，將 `Customers` 資料表中的第一個資料列標記為已刪除：

     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]

## <a name="determine-if-there-are-changed-rows"></a>判斷是否有變更的資料列
 對資料集中的記錄進行變更時，這些變更的相關資訊會儲存到您認可它們為止。 當您呼叫資料集或資料表的 `AcceptChanges` 方法，或是呼叫 TableAdapter 或資料介面卡的 `Update` 方法時，就會認可變更。

 在每個資料列中，追蹤變更的方式有兩種：

- 每個資料列都包含其 <xref:System.Data.DataRow.RowState%2A> 的相關資訊（例如，<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState> 或 <xref:System.Data.DataRowState>）。

- 每個已變更的資料列都包含該資料列的多個版本（<xref:System.Data.DataRowVersion>）、原始版本（變更前）和目前版本（變更之後）。 在暫止變更的期間（您可以回應 <xref:System.Data.DataTable.RowChanging> 事件的時間），也會提供第三個版本（也就是建議的版本）。

  如果資料集內已進行變更，資料集的 <xref:System.Data.DataSet.HasChanges%2A> 方法會傳回 `true`。 判斷變更的資料列存在之後，您可以呼叫 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 的 `GetChanges` 方法，以傳回一組已變更的資料列。 如需詳細資訊，請參閱[如何：取出已變更](https://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)的資料列。

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>判斷是否已對任何資料列進行變更

- 呼叫資料集的 <xref:System.Data.DataSet.HasChanges%2A> 方法，以檢查是否有變更的資料列。

     下列範例示範如何檢查 <xref:System.Data.DataSet.HasChanges%2A> 方法的傳回值，以偵測名為 `NorthwindDataset1` 的資料集是否有任何已變更的資料列：

     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]

## <a name="determine-the-type-of-changes"></a>判斷變更的類型
 您也可以藉由將值從 <xref:System.Data.DataRowState> 列舉傳遞至 <xref:System.Data.DataSet.HasChanges%2A> 方法，檢查資料集所做的變更類型。

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>判斷資料列已進行了何種類型的變更

- 將 <xref:System.Data.DataRowState> 值傳遞給 <xref:System.Data.DataSet.HasChanges%2A> 方法。

     下列範例顯示如何檢查名為 `NorthwindDataset1` 的資料集，以判斷是否已加入任何新的資料列：

     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]

## <a name="to-locate-rows-that-have-errors"></a>找出有錯誤的資料列
 使用個別資料行和資料列時，您可能會遇到錯誤。 您可以檢查 `HasErrors` 屬性，以判斷 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或 <xref:System.Data.DataRow> 中是否有錯誤。

1. 檢查 `HasErrors` 屬性，以查看資料集中是否有任何錯誤。

2. 如果 `HasErrors` 屬性是 `true`，請逐一查看資料表的集合，然後逐一查看資料列，以尋找具有錯誤的資料列。

     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]
