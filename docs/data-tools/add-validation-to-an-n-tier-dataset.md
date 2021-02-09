---
title: 將驗證新增至多層式架構 (N-Tier) 資料集
description: 在 Visual Studio 中，將驗證加入至多層式資料集。 驗證個別資料行或整個資料列的變更。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 4911cc5ced991389d2c7b03a405c4fe9e28c5cc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859355"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>將驗證新增至多層式架構 (N-Tier) 資料集
將驗證加入至多層式方案的資料集，基本上與將驗證新增至單一檔案資料集 (單一專案) 中的資料集相同。 針對資料執行驗證的建議位置是在 <xref:System.Data.DataTable.ColumnChanging> 資料表格的和/或 <xref:System.Data.DataTable.RowChanging> 事件期間。

資料集提供建立部分類別的功能，您可以將使用者程式碼加入至資料集內資料表的資料行和資料列變更事件。 如需在多層式方案中將程式碼加入至資料集的詳細資訊，請參閱 [將程式碼加入至多層式應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md)，並 [將程式碼加入至多層式應用程式中的 tableadapter](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)。 如需部分類別的詳細資訊，請參閱 [如何：將類別分割成部分類別 (類別設計工具) ](../ide/class-designer/how-to-split-a-class-into-partial-classes.md) 或 [部分類別和方法](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)。

> [!NOTE]
> 當您藉由設定 [ **資料集專案** ] 屬性) 來分隔 tableadapter (中的資料集時，不會自動移動專案中的現有部分資料集類別。 您必須手動將現有的部分資料集類別移至資料集專案。

> [!NOTE]
> Dataset 設計工具不會自動以 c # 為和事件建立事件處理常式 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> 。 您必須手動建立事件處理常式，並將事件處理常式連結到基礎事件。 下列程式描述如何在 Visual Basic 和 c # 中建立必要的事件處理常式。

## <a name="validate-changes-to-individual-columns"></a>驗證個別資料行的變更
藉由處理事件來驗證個別資料行中的值 <xref:System.Data.DataTable.ColumnChanging> 。 <xref:System.Data.DataTable.ColumnChanging>修改資料行中的值時，就會引發事件。 <xref:System.Data.DataTable.ColumnChanging>在 **DataSet 設計工具** 上按兩下所需的資料行，以建立事件的事件處理常式。

當您第一次按兩下資料行時，設計工具會產生事件的事件處理常式 <xref:System.Data.DataTable.ColumnChanging> 。 `If...Then`此外也會建立一個語句，以測試特定的資料行。 例如，當您按兩下 Northwind Orders 資料表上的 [已產生 **日期** ] 資料行時，就會產生下列程式碼：

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> 在 c # 專案中，DataSet 設計工具只會在資料集中建立資料集和個別資料表的部分類別。 DataSet 設計工具不會在 c # 中自動建立和事件的事件處理常式， <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> 就像在 Visual Basic 中一樣。 在 c # 專案中，您必須手動建立方法來處理事件，並將方法連結至基礎事件。 下列程式提供在 Visual Basic 和 c # 中建立所需事件處理常式的步驟。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>在變更個別資料行值期間加入驗證

1. 在 **方案總管** 中按兩下 *.xsd* 檔來開啟資料集。 如需詳細資訊，請參閱 [逐步解說：在 DataSet 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。

2. 按兩下要驗證的資料行。 此動作會建立 <xref:System.Data.DataTable.ColumnChanging> 事件處理常式。

    > [!NOTE]
    > DataSet 設計工具不會自動建立 c # 事件的事件處理常式。 下一節包含以 c # 處理事件所需的程式碼。 `SampleColumnChangingEvent` 會建立，然後連接到 <xref:System.Data.DataTable.ColumnChanging> 方法中的事件 <xref:System.Data.DataTable.EndInit%2A> 。

3. 加入程式碼，以確認是否 `e.ProposedValue` 包含符合您應用程式需求的資料。 如果無法接受建議的值，請設定資料行以表示它包含錯誤。

     下列程式碼範例會驗證 **Quantity** 資料行是否包含大於0的值。 如果 **Quantity** 小於或等於0，則會將資料行設定為錯誤。 `Else`如果 **Quantity** 超過0，子句會清除錯誤。 資料行變更事件處理常式中的程式碼應該如下所示：

    ```vb
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then
        If CType(e.ProposedValue, Short) <= 0 Then
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")
        Else
            e.Row.SetColumnError(e.Column, "")
        End If
    End If
    ```

    ```csharp
    // Add this code to the DataTable partial class.

    public override void EndInit()
    {
        base.EndInit();
        // Hook up the ColumnChanging event
        // to call the SampleColumnChangingEvent method.
        ColumnChanging += SampleColumnChangingEvent;
    }

    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)
    {
        if (e.Column.ColumnName == QuantityColumn.ColumnName)
        {
            if ((short)e.ProposedValue <= 0)
            {
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
            }
            else
            {
                e.Row.SetColumnError("Quantity", "");
            }
        }
    }
    ```

## <a name="validate-changes-to-whole-rows"></a>驗證整個資料列的變更
藉由處理事件來驗證整個資料列中的值 <xref:System.Data.DataTable.RowChanging> 。 <xref:System.Data.DataTable.RowChanging>認可所有資料行中的值時，就會引發事件。 <xref:System.Data.DataTable.RowChanging>當某個資料行中的值相依于另一個資料行中的值時，就必須在事件中進行驗證。 例如，請考慮在 Northwind 的 Orders 資料表中的日期和要求。

當輸入訂單時，驗證會確定訂單未輸入具有日期時間或之前的日期時間。 在此範例中，必須比較「要求規定」和「日期日期」資料行的值，因此驗證個別資料行變更並不合理。

<xref:System.Data.DataTable.RowChanging>按兩下 **DataSet 設計工具** 上資料表標題列中的資料表名稱，即可建立事件的事件處理常式。

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>若要在整個資料列變更期間加入驗證

1. 在 **方案總管** 中按兩下 *.xsd* 檔來開啟資料集。 如需詳細資訊，請參閱 [逐步解說：在 DataSet 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。

2. 按兩下設計工具上資料表的標題列。

     部分類別是使用 `RowChanging` 事件處理常式所建立，並在程式碼編輯器中開啟。

    > [!NOTE]
    > DataSet 設計工具不會 <xref:System.Data.DataTable.RowChanging> 在 c # 專案中自動建立事件的事件處理常式。 您必須建立方法來處理 <xref:System.Data.DataTable.RowChanging> 事件並執行程式碼，然後將事件連結至資料表的初始化方法。

3. 在部分類別宣告中加入使用者程式碼。

4. 下列程式碼會顯示在事件期間要如何加入使用者程式碼以進行驗證的位置 <xref:System.Data.DataTable.RowChanging> 。 C # 範例也包含將事件處理常式方法連結至事件的程式碼 `OrdersRowChanging` 。

    ```vb
    Partial Class OrdersDataTable
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging
            ' Add logic to validate columns here.
            If e.Row.RequiredDate <= e.Row.OrderDate Then
                ' Set the RowError if validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"
            Else
                ' Clear the RowError when validation passes.
                e.Row.RowError = ""
            End If
        End Sub
    End Class
    ```

    ```csharp
    partial class OrdersDataTable
    {
        public override void EndInit()
        {
            base.EndInit();
            // Hook up the event to the
            // RowChangingEvent method.
            OrdersRowChanging += RowChangingEvent;
        }

        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)
        {
            // Perform the validation logic.
            if (e.Row.RequiredDate <= e.Row.OrderDate)
            {
                // Set the row to an error when validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";
            }
            else
            {
                // Clear the RowError if validation passes.
                e.Row.RowError = "";
            }
        }
    }
    ```

## <a name="see-also"></a>另請參閱

- [多層式資料應用程式總覽](../data-tools/n-tier-data-applications-overview.md)
- [逐步解說：建立多層式資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [驗證資料集中的資料](../data-tools/validate-data-in-datasets.md)
