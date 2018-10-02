---
title: 如何： 執行傳回單一值的預存程序 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CommandType.StoredProcedure
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- ExecuteReader method example [Visual Basic]
- stored procedures, examples
- stored procedures, executing
ms.assetid: ecf8c262-58ca-4a69-a82c-916c0c061422
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 00e5f497a01d6600d02f3de42aa487819e4dac45
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499136"
---
# <a name="how-to-execute-a-stored-procedure-that-returns-a-single-value"></a>如何：執行傳回單一值的預存程序
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要執行傳回單一值的預存程序，您可以執行 TableAdapter 查詢設定為執行預存程序 (例如`CustomersTableAdapter.CustomerCount()`)。  
  
 如果您的應用程式不會使用 TableAdapters，呼叫`ExecuteScalar`方法，在命令物件，設定其`CommandType`屬性設<xref:System.Data.CommandType>。 (「 命令物件 」 是指針對特定的命令[.NET Framework Data Provider](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)應用程式所使用。 例如，如果您的應用程式使用.NET Framework Data Provider for SQL Server，命令的物件會<xref:System.Data.SqlClient.SqlCommand>。)  
  
 下列範例示範如何執行使用任一個 TableAdapters，從資料庫傳回單一值的預存程序或指令的物件。 如需有關如何使用 Tableadapter 和命令進行查詢的詳細資訊，請參閱[使用 Tableadapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-stored-procedures-that-return-single-values-using-a-tableadapter"></a>執行預存程序會傳回單一值，使用 TableAdapter  
 此範例示範如何建立 TableAdapter 查詢 using[編輯 TableAdapters](../data-tools/editing-tableadapters.md)，然後宣告 TableAdapter 的執行個體及執行查詢的方式提供資訊。  
  
#### <a name="to-execute-a-stored-procedure-that-returns-a-single-value-using-a-tableadapter"></a>若要執行傳回單一值，使用 TableAdapter 的預存程序  
  
1.  開啟中的資料集**Dataset 設計工具**。 如需詳細資訊，請參閱 <<c0> [ 如何： 以 Dataset 設計工具中開啟資料集](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。  
  
2.  如果您還沒有一個建立的 TableAdapter。 如需有關如何建立 Tableadapter 的詳細資訊，請參閱 <<c0> [ 建立和設定 Tableadapter](../data-tools/create-and-configure-tableadapters.md)。  
  
3.  如果您已經有一個查詢，您會使用預存程序傳回單一值的 TableAdapter 上，請跳至下一個程序，「 宣告 TableAdapter 的執行個體，並執行查詢。 」 否則，請繼續進行步驟 4，以建立新的查詢會傳回單一值。  
  
4.  以滑鼠右鍵按一下您想要的 TableAdapter，並加入查詢中使用的捷徑功能表。  
  
     **TableAdapter 查詢組態精靈**隨即開啟。  
  
5.  選取 [**使用現有的預存程序**，然後按一下**下一步]**。  
  
6.  從下拉式清單中，選取預存程序，然後按一下**下一步**。  
  
7.  選取選項來傳回**的單一值**，然後按一下**下一步**。  
  
8.  提供查詢名稱。  
  
9. 按一下 [**下一步]** 或是**完成**以完成精靈，將查詢加入至 TableAdapter。  
  
10. 建置您的專案。  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>若要宣告 TableAdapter 的執行個體，並執行查詢  
  
1.  宣告 TableAdapter，其中包含您想要執行的查詢執行的個體。  
  
    -   若要建立使用設計階段工具的執行個體，拖曳您想從 TableAdapter**工具箱**。 (在專案中的元件現在都會出現在**工具箱**符合您的專案名稱的標題之下。)如果未出現在 TableAdapter**工具箱**，則您可能需要建置您的專案。  
  
         -或-  
  
    -   若要在程式碼中建立執行個體，取代下列程式碼的名稱與您<xref:System.Data.DataSet>和 TableAdapter。  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Tableadapter 實際上不會在其相關聯的資料集類別。 每個資料集有它自己的命名空間中的 TableAdapters 對應集合。 例如，如果您擁有名為資料集`SalesDataSet`，會有`SalesDataSetTableAdapters`包含其 TableAdapters 的命名空間。  
  
2.  呼叫您的查詢，如程式碼中呼叫其他方法一樣。 您的查詢是 TableAdapter 上的方法。 下列程式碼取代為 TableAdapter 和查詢的名稱。 您也必須在您的查詢所需的任何參數中傳遞。 如果您不確定，如果您的查詢需要參數，或哪些參數，它需要，然後檢查有無 IntelliSense 的查詢所需的簽章。 根據查詢是否會接受參數與否，程式碼看起來會類似下列範例的其中一項：  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     若要宣告 TableAdapter 的執行個體，並執行查詢的完整程式碼看起來應該如下所示：  
  
     [!code-csharp[VbRaddataFillingAndExecuting#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#9)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#9)]  
  
## <a name="executing-stored-procedures-that-return-single-values-using-a-command-object"></a>執行預存程序會傳回單一值使用的 Command 物件  
 下列範例示範如何建立命令並將執行傳回單一值的預存程序。 如需設定和取得命令的參數值的資訊，請參閱[如何： 設定和取得命令物件的參數](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)。  
  
 這個範例會使用<xref:System.Data.SqlClient.SqlCommand>物件，並需要：  
  
-   若要參考<xref:System>， <xref:System.Data>，和<xref:System.Xml>命名空間。  
  
-   資料連接名為`SqlConnection1`。  
  
-   一個名為資料表`Customers`在資料來源，`SqlConnection1`會連線到。 （否則您需要有效的 SQL 陳述式為資料來源）。  
  
#### <a name="to-execute-a-stored-procedure-that-returns-a-single-value-using-a-datacommand"></a>若要執行傳回單一值，使用需要的預存程序  
  
-   將下列程式碼新增至您想要執行的程式碼的方法。 您藉由呼叫傳回單一數值`ExecuteScalar`命令的方法 (例如<xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>)。 在傳回的資料`object`。  
  
     [!code-csharp[VbRaddataFillingAndExecuting#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#14)]
     [!code-vb[VbRaddataFillingAndExecuting#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#14)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [如何： 建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)   
 [如何： 編輯 TableAdapter 查詢](../data-tools/how-to-edit-tableadapter-queries.md)   
 [如何： 使用資料填入資料集](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [使用 Tableadapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [如何： 設定及取得命令物件的參數](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)