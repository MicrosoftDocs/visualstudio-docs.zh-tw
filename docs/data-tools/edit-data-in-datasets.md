---
title: 編輯資料集中的資料
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fe59b30e9af7ee1d98c0aba65339af1d53cba8fb
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282458"
---
# <a name="edit-data-in-datasets"></a>編輯資料集中的資料
編輯資料表中的資料，就像您在任何資料庫中編輯資料表中的資料一樣。 此程式可以包含插入、更新和刪除資料表中的記錄。 在資料系結表單中，您可以指定哪些欄位可供使用者編輯。 在這些情況下，資料系結基礎結構會處理所有變更追蹤，以便稍後將變更傳送回資料庫。 如果您以程式設計方式對資料進行編輯，而且想要將這些變更傳回至資料庫，則必須使用為您執行變更追蹤的物件和方法。

除了變更實際資料以外，您也可以查詢 <xref:System.Data.DataTable> 來傳回特定的資料列。 例如，您可以查詢個別的資料列、特定的資料列版本（原始和建議的資料列）、已變更的資料列，或有錯誤的資料列。

## <a name="to-edit-rows-in-a-dataset"></a>編輯資料集中的資料列
若要編輯中的現有 <xref:System.Data.DataTable> 資料列，您需要找出 <xref:System.Data.DataRow> 您想要編輯的，然後將更新的值指派給所需的資料行。

如果您不知道想要編輯之資料列的索引，請使用 `FindBy` 方法，依主鍵進行搜尋：

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

如果您知道資料列索引，您可以存取和編輯資料列，如下所示：

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>若要將新的資料列插入 dataset
使用資料繫結控制項的應用程式通常會透過[BindingNavigator 控制項](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms)上的 [**加入新**的] 按鈕來加入新的記錄。

若要手動將新記錄加入至資料集，請在 DataTable 上呼叫方法來建立新的資料列。 然後，將該資料列新增至的 <xref:System.Data.DataRow> 集合（ <xref:System.Data.DataTable.Rows%2A> ） <xref:System.Data.DataTable> ：

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

若要保留資料集將更新傳送至資料來源所需的資訊，請使用方法， <xref:System.Data.DataRow.Delete%2A> 移除資料表中的資料列。 例如，如果您的應用程式使用 TableAdapter （或 <xref:System.Data.Common.DataAdapter> ），TableAdapter 的 `Update` 方法會刪除資料庫中具有之的資料列 <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted> 。

如果您的應用程式不需要將更新傳送回資料來源，則可以直接存取資料列集合（）來移除記錄 <xref:System.Data.DataRowCollection.Remove%2A> 。

#### <a name="to-delete-records-from-a-data-table"></a>若要從資料表中刪除記錄

- 呼叫的 <xref:System.Data.DataRow.Delete%2A> 方法 <xref:System.Data.DataRow> 。

     這個方法不會實際移除記錄。 相反地，它會標示要刪除的記錄。

    > [!NOTE]
    > 如果您取得的 count 屬性 <xref:System.Data.DataRowCollection> ，產生的計數會包含已標示為要刪除的記錄。 若要取得未標示為要刪除之記錄的精確計數，您可以對集合進行迴圈查看 <xref:System.Data.DataRow.RowState%2A> 每一筆記錄的屬性。 （標記為刪除的記錄具有 <xref:System.Data.DataRow.RowState%2A> 的 <xref:System.Data.DataRowState.Deleted> 。）或者，您也可以建立資料集的資料檢視，以便根據資料列狀態進行篩選，並從該處取得 count 屬性。

下列範例示範如何呼叫 <xref:System.Data.DataRow.Delete%2A> 方法，將資料表中的第一個資料列標記 `Customers` 為已刪除：

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>判斷是否有變更的資料列
對資料集中的記錄進行變更時，這些變更的相關資訊會儲存到您認可它們為止。 當您呼叫 `AcceptChanges` 資料集或資料表的方法時，或當您呼叫 `Update` TableAdapter 或資料介面卡的方法時，您會認可變更。

在每個資料列中，追蹤變更的方式有兩種：

- 每個資料列都包含與其相關的資訊（例如、、 <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Added> <xref:System.Data.DataRowState.Modified> <xref:System.Data.DataRowState.Deleted> 或 <xref:System.Data.DataRowState.Unchanged> ）。

- 每個已變更的資料列都包含該資料列的多個版本（ <xref:System.Data.DataRowVersion> ）、原始版本（變更前）和目前版本（變更之後）。 在變更暫止的期間（您可以回應事件的時間 <xref:System.Data.DataTable.RowChanging> ），也會提供第三個版本（也就是建議的版本）。

<xref:System.Data.DataSet.HasChanges%2A> `true` 如果資料集內已進行變更，則資料集的方法會傳回。 判斷變更的資料列存在之後，您可以呼叫 `GetChanges` 或的方法 <xref:System.Data.DataSet> ， <xref:System.Data.DataTable> 以傳回一組已變更的資料列。

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>判斷是否已對任何資料列進行變更

- 呼叫 <xref:System.Data.DataSet.HasChanges%2A> 資料集的方法，以檢查是否有變更的資料列。

下列範例顯示如何檢查方法的傳回值 <xref:System.Data.DataSet.HasChanges%2A> ，以偵測資料集內是否有任何已變更的資料列 `NorthwindDataset1` ：

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>判斷變更的類型
您也可以藉由將列舉中的值傳遞給方法，來查看資料集內所做的變更類型 <xref:System.Data.DataRowState> <xref:System.Data.DataSet.HasChanges%2A> 。

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>判斷資料列已進行了何種類型的變更

- 將 <xref:System.Data.DataRowState> 值傳遞給 <xref:System.Data.DataSet.HasChanges%2A> 方法。

下列範例顯示如何檢查名為的資料集 `NorthwindDataset1` ，以判斷是否有任何新的資料列新增至其中：

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>找出有錯誤的資料列
使用個別資料行和資料列時，您可能會遇到錯誤。 您可以檢查 `HasErrors` 屬性，以判斷、或中是否有 <xref:System.Data.DataSet> 錯誤 <xref:System.Data.DataTable> <xref:System.Data.DataRow> 。

1. 檢查 `HasErrors` 屬性，以查看資料集中是否有任何錯誤。

2. 如果 `HasErrors` 屬性為 `true` ，請逐一查看資料表的集合，然後逐一查看資料列，以尋找具有錯誤的資料列。

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
