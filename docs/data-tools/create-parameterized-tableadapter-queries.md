---
title: 建立參數型的 TableAdapter 查詢
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e65809d479c9cac40d7d4c79066e8becd81b09b6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="create-parameterized-tableadapter-queries"></a>建立參數型的 TableAdapter 查詢
參數型查詢會傳回符合查詢中 WHERE 子句條件的資料。 例如，您可以將 `WHERE City = @City` 加入至傳回客戶清單的 SQL 陳述式結尾，以參數化客戶清單，使其只顯示特定城市的客戶。

 建立參數型的 TableAdapter 查詢中**Dataset 設計工具**。您也可以建立它們在 Windows 應用程式中使用**參數化資料來源**命令**資料**功能表。 **參數化資料來源**命令會建立您的表單，您可以在其中輸入參數值並執行查詢上的控制項。

> [!NOTE]
> 當建構參數化的查詢時，使用參數標記法的特定至您的撰寫語言針對資料庫。 例如，Access 和 OleDb 資料來源使用問號 '?' 代表參數，所以 WHERE 子句應該類似：`WHERE City = ?`。

> [!NOTE]
> 對話方塊與功能表命令，您會看到可能與根據您目前使用的設定或版本，您所使用的 [說明] 中描述的不同。 若要變更您的設定，請移至**工具**功能表，然後選取**匯入和匯出設定**。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="create-a-parameterized-tableadapter-query"></a>建立參數型的 TableAdapter 查詢

#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>在 DataSet 設計工具中建立參數型查詢

-   建立新的 TableAdapter，並將具有所需參數的 WHERE 子句加入至 SQL 陳述式。 如需詳細資訊，請參閱[建立及設定 Tableadapter](../data-tools/create-and-configure-tableadapters.md)。

     -或-

-   將查詢加入至現有 TableAdapter，並將具有所需參數的 WHERE 子句加入至 SQL 陳述式。

#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>在設計資料繫結表單時建立參數型查詢

1.  在表單上選取已繫結至資料集的控制項。 如需詳細資訊，請參閱[繫結 Windows Form 控制項加入 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)。

2.  在**資料**功能表上，選取**加入查詢**。

3.  完成**搜尋準則產生器**對話方塊中，將具有所需參數的 WHERE 子句加入至 SQL 陳述式。

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>將查詢加入至現有的資料繫結表單

1.  開啟表單中的**Windows Form 設計工具**。

2.  在**資料**功能表上，選取**加入查詢**或**資料智慧標籤**。

    > [!NOTE]
    >  如果**加入查詢**並不適用於**資料**功能表中，選取想要加入參數化的顯示的資料來源您表單上的控制項。 例如，若表單以 <xref:System.Windows.Forms.DataGridView> 控制項顯示資料，請選取此控制項。 若表單以個別控制項顯示資料，請選取任何資料繫結控制項。

3.  在**選取資料來源資料表**區域中，選取您想要的資料表加入至參數化。

4.  中輸入名稱**新的查詢名稱**方塊，如果您要建立新的查詢。

     -或-

     選取查詢中的**現有的查詢名稱**方塊。

5.  在**查詢文字**方塊中，輸入採用參數的查詢。

6.  選取 [確定]。

     輸入參數的控制項和**負載**按鈕加入到表單中<xref:System.Windows.Forms.ToolStrip>控制項。

#### <a name="querying-for-null-values"></a>Null 值的查詢
當您想要查詢的記錄沒有目前的值時，TableAdapter 參數可以指派 null 值。 例如，請考慮下列查詢具有`ShippedDate`參數在其`WHERE`子句：

 ```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

 如果這是 TableAdapter 上的查詢，您無法查詢未以下列程式碼已寄出的所有訂單：

 [!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
 [!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

 若要啟用查詢接受 null 值：

1.  在**Dataset 設計工具**，選取要接受 null 的參數值的 TableAdapter 查詢。

2.  在**屬性**視窗中，選取**參數**，然後按一下省略符號 (**...**) 按鈕來開啟**參數集合編輯器**。

3.  選取 允許 null 值的參數，並設定**AllowDbNull**屬性`true`。

## <a name="see-also"></a>另請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)