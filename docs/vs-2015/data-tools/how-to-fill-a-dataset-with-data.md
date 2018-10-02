---
title: 如何： 使用資料填入資料集 |Microsoft Docs
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
- TableAdapter.GetData
- TableAdapter.Fill
- datasets [Visual Basic], filling
- DataTable objects, loading
- data [Visual Basic], loading into datasets
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: c2bba5c7bcdf1453129c6c3677e750c0e5599bac
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491548"
---
# <a name="how-to-fill-a-dataset-with-data"></a>如何： 使用資料填入資料集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

片語 「 以資料填入資料集 」 是指將資料載入至個別<xref:System.Data.DataTable>組成資料集的物件。 藉由執行 TableAdapter 查詢或藉由執行資料配接器，填入資料的資料表 (例如<xref:System.Data.SqlClient.SqlDataAdapter>) 命令。  
  
 您是否應使用 Tableadapter 或資料配接器，端視您建立資料集的方式而定。 如果您使用中的設計工具[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，這類[資料來源組態精靈](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)，您的資料集包含 Tableadapter。 如需有關 TableAdapters 的詳細資訊，請參閱[TableAdapter 概觀](../data-tools/tableadapter-overview.md)。 如果您以程式設計方式建立您的資料集，您通常要建立資料配接器，將資料載入資料表。  
  
> [!NOTE]
>  當項目從[資料來源 視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)拖曳至表單，將資料填入資料表的程式碼會自動新增至`Form_Load`事件處理常式。 若要查看確切的語法來填滿您的特定資料表的程式碼編輯器中開啟您的表單。 如果您不想要填入資料表，當表單載入時，您可以將此程式碼移至其他方法，或將它完全移除。  
  
## <a name="filling-a-dataset-using-a-tableadapter"></a>填入資料集使用 TableAdapter  
 您可以將資料載入資料表中的資料集 TableAdapter 上呼叫的查詢。 傳遞<xref:System.Data.DataTable>要填滿至 TableAdapter 查詢。 如果您的查詢不接受參數，將這些參數傳遞給方法以及。 如果資料集包含多個資料表，您應該針對每個資料表的個別 Tableadapter，並因此必須另外填入每個資料表。  
  
> [!NOTE]
>  根據預設，每次執行 TableAdapter 查詢時，資料表中的資料清除之前正在載入資料表中查詢的結果。 您可以將現有的資料保留在資料表，並將結果附加藉由設定 TableAdapter`ClearBeforeFill`屬性設`false`。  
  
#### <a name="to-fill-a-dataset-with-data-using-a-tableadapter"></a>若要使用 TableAdapter 與資料填入資料集  
  
1.  開啟您的表單或磢咘**程式碼編輯器**。  
  
2.  在您要將資料載入資料表資料的應用程式中的任一處加入程式碼。 如果您的查詢不接受參數，傳入<xref:System.Data.DataTable>要填滿。 程式碼看起來應該如下所示：  
  
     [!code-csharp[VbRaddataFillingAndExecuting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#4)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#4)]  
  
3.  如果您的查詢不接受參數，傳入<xref:System.Data.DataTable>要填滿] 與 [查詢所需的參數。 在查詢中的實際參數，根據程式碼會看起來會類似下列範例：  
  
     [!code-csharp[VbRaddataFillingAndExecuting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#5)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#5)]  
  
## <a name="filling-a-dataset-using-a-dataadapter"></a>填入資料集使用資料配接器  
 呼叫資料配接器的`Fill`方法。 這會導致配接器來執行 SQL 陳述式或預存程序中參考其`SelectCommand`屬性並將結果放入資料集內的資料表。 如果資料集包含多個資料表，您應該有個別的資料配接器，每個資料表，並因此必須分別填入每個資料表。  
  
#### <a name="to-fill-a-dataset-with-data-using-a-dataadapter"></a>若要使用資料配接器的資料填入資料集  
  
-   呼叫<xref:System.Data.Common.DataAdapter.Fill%2A>方法<xref:System.Data.Common.DataAdapter>，並傳入<xref:System.Data.DataSet>或<xref:System.Data.DataTable>將資料載入。 例如:   
  
     [!code-csharp[VbRaddataFillingAndExecuting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#6)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#6)]  
  
     您通常應該提供的名稱<xref:System.Data.DataTable>將資料載入。 如果您傳遞名稱<xref:System.Data.DataSet>而不是特定的資料表，<xref:System.Data.DataTable>名為`Table1`加入至資料集，並載入從資料庫產生的結果 (而非在現有資料的載入<xref:System.Data.DataTable>資料集內)。 如需詳細資訊，請參閱 <<c0> [ 從 DataAdapter 填入 DataSet](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Tableadapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [將資料擷取至您的應用程式](../data-tools/fetching-data-into-your-application.md)   
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [儲存資料](../data-tools/saving-data.md)