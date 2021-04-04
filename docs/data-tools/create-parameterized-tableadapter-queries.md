---
title: 建立參數型 TableAdapter 查詢
description: 瞭解如何建立參數化的 TableAdapter 查詢。 參數型查詢會傳回符合查詢中 WHERE 子句條件的資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: d747459abc62462864e94ed9b8af9b11c6b9eabe
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215926"
---
# <a name="create-parameterized-tableadapter-queries"></a>建立參數型 TableAdapter 查詢

參數型查詢會傳回符合查詢中 WHERE 子句條件的資料。 例如，您可以將 `WHERE City = @City` 加入至傳回客戶清單的 SQL 陳述式結尾，以參數化客戶清單，使其只顯示特定城市的客戶。

您可以在 **DataSet 設計工具** 中建立參數化的 TableAdapter 查詢。您也可以使用 [**資料**] 功能表上的 [**參數化資料來源**] 命令，在 Windows 應用程式中建立它們。 **參數化資料來源** 命令會在您的表單上建立控制項，您可以在其中輸入參數值並執行查詢。

> [!NOTE]
> 當您建立參數化查詢時，請使用您要撰寫程式碼的資料庫專用的參數標記法。 例如，Access 和 OleDb 資料來源使用問號 '?' 代表參數，所以 WHERE 子句應該類似：`WHERE City = ?`。

## <a name="create-a-parameterized-tableadapter-query"></a>建立參數型 TableAdapter 查詢

### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>在 DataSet 設計工具中建立參數型查詢

- 建立新的 TableAdapter，並將具有所需參數的 WHERE 子句加入至 SQL 陳述式。 如需詳細資訊，請參閱 [建立和設定 tableadapter](../data-tools/create-and-configure-tableadapters.md)。

     -或-

- 將查詢加入至現有 TableAdapter，並將具有所需參數的 WHERE 子句加入至 SQL 陳述式。

### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>在設計資料繫結表單時建立參數型查詢

1. 在表單上選取已繫結至資料集的控制項。 如需詳細資訊，請參閱 [將 Windows Forms 控制項系結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)。

2. 選取 [ **資料** ] 功能表上的 [ **加入查詢**]。

3. 完成 [搜尋準則產生器] 對話方塊，並將具有所需參數的 WHERE 子句新增至 SQL 陳述式。

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>將查詢加入至現有的資料繫結表單

1. 在 **Windows Forms 設計工具** 中開啟表單。

2. 在 [ **資料** ] 功能表上，選取 [ **加入查詢** ] 或 [ **資料智慧標籤**]。

    > [!NOTE]
    > 若 [資料] 功能表中的 [新增查詢] 無法使用，請選取表單上顯示您想要新增參數化之資料來源的控制項。 例如，若表單以 <xref:System.Windows.Forms.DataGridView> 控制項顯示資料，請選取此控制項。 若表單以個別控制項顯示資料，請選取任何資料繫結控制項。

3. 在 [ **選取資料來源資料表** ] 區域中，選取您要加入參數化的資料表。

4. 如果您要建立新查詢，請在 [新的查詢名稱] 方塊中鍵入名稱。

     -或-

     選取 [現有的查詢名稱] 方塊中的查詢。

5. 在 [ **查詢] 文字方塊** 中，輸入接受參數的查詢。

6. 選取 [確定]。

     輸入參數的控制項及 [載入] 按鈕會新增至 <xref:System.Windows.Forms.ToolStrip> 控制項中的表單。

### <a name="query-for-null-values"></a>查詢 null 值

當您想要查詢目前沒有值的記錄時，可以將 TableAdapter 參數指派給 null 值。 例如，請考慮下列在 `ShippedDate` 其子句中有參數的查詢 `WHERE` ：

```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

如果這是對 TableAdapter 的查詢，您可以查詢尚未隨附于下列程式碼中的所有訂單：

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs" id="Snippet8":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb" id="Snippet8":::

若要讓查詢接受 null 值：

1. 在 [ **DataSet 設計工具** 中，選取需要接受 null 參數值的 TableAdapter 查詢。

2. 在 [ **屬性** ] 視窗中，選取 [ **參數**]，然後按一下省略號 (**...**) 按鈕以開啟 [ **參數集合編輯器**]。

3. 選取允許 null 值的參數，並將 **AllowDbNull** 屬性設定為 `true` 。

## <a name="see-also"></a>另請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)
