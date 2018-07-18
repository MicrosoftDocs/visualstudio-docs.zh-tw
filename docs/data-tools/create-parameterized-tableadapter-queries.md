---
title: 建立參數型 TableAdapter 查詢
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
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fe77d3622e9c41d98ff89972e522bb25aae58b9d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756005"
---
# <a name="create-parameterized-tableadapter-queries"></a>建立參數型 TableAdapter 查詢
參數型查詢會傳回符合查詢中 WHERE 子句條件的資料。 例如，您可以將 `WHERE City = @City` 加入至傳回客戶清單的 SQL 陳述式結尾，以參數化客戶清單，使其只顯示特定城市的客戶。

 建立中的參數型的 TableAdapter 查詢**Dataset 設計工具**。您也可以建立其與 Windows 應用程式中**參數化資料來源**命令**資料**功能表。 **參數化資料來源**命令會建立您的表單，您可以在此輸入參數值，並執行查詢上的控制項。

> [!NOTE]
> 當建構參數化的查詢時，使用參數標記法的特定資料庫正在編寫。 例如，Access 和 OleDb 資料來源使用問號 '?' 代表參數，所以 WHERE 子句應該類似：`WHERE City = ?`。

> [!NOTE]
> 對話方塊和功能表命令，您會看到，可能會有所不同說明中所述，根據您目前使用的設定或您使用的版本不同。 若要變更您的設定，請前往**工具**功能表，然後選取**匯入和匯出設定**。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="create-a-parameterized-tableadapter-query"></a>建立參數型的 TableAdapter 查詢

#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>在 DataSet 設計工具中建立參數型查詢

-   建立新的 TableAdapter，並將具有所需參數的 WHERE 子句加入至 SQL 陳述式。 如需詳細資訊，請參閱 <<c0> [ 建立和設定 Tableadapter](../data-tools/create-and-configure-tableadapters.md)。

     -或-

-   將查詢加入至現有 TableAdapter，並將具有所需參數的 WHERE 子句加入至 SQL 陳述式。

#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>在設計資料繫結表單時建立參數型查詢

1.  在表單上選取已繫結至資料集的控制項。 如需詳細資訊，請參閱 <<c0> [ 繫結 Windows Form 控制項加入 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)。

2.  在 **資料**功能表上，選取**加入查詢**。

3.  完成**搜尋準則產生器**對話方塊中，將 WHERE 子句加入具有所需參數的 SQL 陳述式。

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>將查詢加入至現有的資料繫結表單

1.  在 **Windows Forms 設計工具**中開啟表單。

2.  在上**資料**功能表上，選取**加入查詢**或是**資料智慧標籤**。

    > [!NOTE]
    >  如果**加入查詢**不適用於**資料**功能表中，選取顯示的資料來源您表單上的控制項要加入至參數化。 例如，若表單以 <xref:System.Windows.Forms.DataGridView> 控制項顯示資料，請選取此控制項。 若表單以個別控制項顯示資料，請選取任何資料繫結控制項。

3.  在 **選取資料來源資料表**區域中，選取您要加入參數化的資料表。

4.  輸入中的名稱**新的查詢名稱**方塊，如果您要建立新的查詢。

     -或-

     選取中的查詢**現有的查詢名稱** 方塊中。

5.  在 **查詢文字**方塊中，輸入採用參數的查詢。

6.  選取 [確定]。

     一個輸入參數的控制項和**負載** 按鈕會新增至表單中<xref:System.Windows.Forms.ToolStrip>控制項。

#### <a name="querying-for-null-values"></a>Null 值的查詢
當您想要查詢的記錄沒有目前的值時，TableAdapter 參數可以指派 null 值。 例如，請考慮下列查詢可`ShippedDate`中的參數及其`WHERE`子句：

 ```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

 如果這是 TableAdapter 的查詢時，您可以查詢尚未運送的下列程式碼的所有訂單：

 [!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
 [!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

 若要啟用查詢，以接受 null 值：

1.  在  **Dataset 設計工具**，選取 TableAdapter 查詢需要接受 null 的參數值。

2.  在 **屬性**視窗中，選取**參數**，然後按一下省略符號 (**...**) 按鈕，即可開啟**參數集合編輯器**。

3.  選取 允許 null 值的參數，並設定**AllowDbNull**屬性設`true`。

## <a name="see-also"></a>另請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)