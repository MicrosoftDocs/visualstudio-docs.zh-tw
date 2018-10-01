---
title: 建立參數型的 TableAdapter 查詢 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 35a2f0c498d6f4239568d4719b2581fdc2f321ea
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486260"
---
# <a name="create-parameterized-tableadapter-queries"></a>建立參數型 TableAdapter 查詢
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[建立參數型 TableAdapter 查詢](https://docs.microsoft.com/visualstudio/data-tools/create-parameterized-tableadapter-queries)。  
  
  
參數型查詢會傳回符合查詢中 WHERE 子句條件的資料。 例如，您可以將 `WHERE City = @City` 加入至傳回客戶清單的 SQL 陳述式結尾，以參數化客戶清單，使其只顯示特定城市的客戶。  
  
 建立中的參數型的 TableAdapter 查詢[Dataset 設計工具](../data-tools/creating-and-editing-typed-datasets.md)。您也可以建立其與 Windows 應用程式中**參數化資料來源**命令**資料**功能表。 **參數化資料來源**命令會建立您的表單，您可以在此輸入參數值，並執行查詢上的控制項。  
  
> [!NOTE]
>  當建構參數化的查詢時，使用參數標記法的特定資料庫正在編寫。 例如，Access 和 OleDb 資料來源使用問號 '?' 代表參數，所以 WHERE 子句應該類似：`WHERE City = ?`。  
  
> [!NOTE]
>  對話方塊和功能表命令，您會看到，可能會有所不同說明中所述，根據您目前使用的設定或您使用的版本不同。 若要變更您的設定，請前往**工具**功能表，然後選取**匯入和匯出設定**。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="create-a-parameterized-tableadapter-query"></a>建立參數型的 TableAdapter 查詢  
  
#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>在 DataSet 設計工具中建立參數型查詢  
  
-   建立新的 TableAdapter，並將具有所需參數的 WHERE 子句加入至 SQL 陳述式。 如需詳細資訊，請參閱 <<c0> [ 建立和設定 Tableadapter](../data-tools/create-and-configure-tableadapters.md)。  
  
     -或-  
  
-   將查詢加入至現有 TableAdapter，並將具有所需參數的 WHERE 子句加入至 SQL 陳述式。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)。  
  
#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>在設計資料繫結表單時建立參數型查詢  
  
1.  在表單上選取已繫結至資料集的控制項。 如需詳細資訊，請參閱 <<c0> [ 繫結 Windows Form 控制項加入 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)。  
  
2.  在 **資料**功能表上，選取**加入查詢**。  
  
3.  完成**搜尋準則產生器**對話方塊中，將 WHERE 子句加入具有所需參數的 SQL 陳述式。  
  
### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>將查詢加入至現有的資料繫結表單  
  
1.  在 **Windows Forms 設計工具**中開啟表單。  
  
2.  在上**資料**功能表上，選取**加入查詢**或是**資料智慧標籤**。  
  
    > [!NOTE]
    >  如果**加入查詢**不適用於**資料**功能表中，選取顯示的資料來源您表單上的控制項要加入至參數化。 例如，若表單以 <xref:System.Windows.Forms.DataGridView> 控制項顯示資料，請選取此控制項。 若表單以個別控制項顯示資料，請選取任何資料繫結控制項。  
  
3.  在 **選取資料來源資料表**區域中，選取您想要 tablethat 新增參數化。  
  
4.  輸入中的名稱**新的查詢名稱**方塊，如果您要建立新的查詢。  
  
     -或-  
  
     選取中的查詢**現有的查詢名稱** 方塊中。  
  
5.  在 **查詢文字**方塊中，輸入採用參數的查詢。  
  
6.  選取 **確定**。  
  
     一個輸入參數的控制項和**負載** 按鈕會新增至表單中<xref:System.Windows.Forms.ToolStrip>控制項。  
  
 當您想要查詢的記錄沒有目前的值時，TableAdapter 參數可以指派 null 值。 例如，請考慮下列查詢可`ShippedDate`中的參數及其`WHERE`子句：  
  
 `SELECT CustomerID, OrderDate, ShippedDate`  
  
 `FROM Orders`  
  
 `WHERE (ShippedDate = @ShippedDate) OR`  
  
 `(ShippedDate IS NULL)`  
  
 如果這是 TableAdapter 的查詢時，您可以查詢尚未運送的下列程式碼的所有訂單：  
  
 [!code-csharp[VbRaddataTableAdapters#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs#8)]
 [!code-vb[VbRaddataTableAdapters#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb#8)]  
  
#### <a name="to-enable-a-query-to-accept-null-values"></a>若要啟用查詢，以接受 null 值  
  
1.  在  **Dataset 設計工具**，選取 TableAdapter 查詢需要接受 null 的參數值。  
  
2.  在 **屬性**視窗中，選取**參數**。然後按 省略符號 (**...**) 按鈕，即可開啟**參數集合編輯器**。  
  
3.  選取 允許 null 值的參數，並設定**AllowDbNull**屬性設`true`。  
  
## <a name="see-also"></a>另請參閱  
 [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)

