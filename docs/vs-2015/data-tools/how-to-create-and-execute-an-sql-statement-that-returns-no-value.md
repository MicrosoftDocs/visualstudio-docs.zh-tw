---
title: 如何： 建立和執行 SQL 陳述式未傳回值 |Microsoft Docs
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
- method calls, examples
- calling methods, examples
- SQL statements, executing
- SQL statements, creating
ms.assetid: 612d3046-0cfa-4d90-be6e-c4d6bcbd5aee
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 2dd78fe0144718337fc589e0d8f8948d5353dd6c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490495"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-no-value"></a>如何：建立及執行未傳回值的 SQL 陳述式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要執行 SQL 陳述式未傳回值，您可以執行 TableAdapter 查詢設定為執行 SQL 陳述式 (例如`CustomersTableAdapter.UpdateTableData(CustomersDataTable)`)。  
  
 如果您的應用程式不會使用 TableAdapters，呼叫`ExecuteNonQuery`方法，在命令物件，設定其`CommandType`屬性設<xref:System.Data.CommandType>。 (「 命令物件 」 是指針對特定的命令[.NET Framework Data Provider](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)應用程式所使用。 例如，如果您的應用程式使用.NET Framework Data Provider for SQL Server，命令的物件會<xref:System.Data.SqlClient.SqlCommand>。)  
  
 下列範例示範如何執行不傳回值使用其中一個 TableAdapters，從資料庫的 SQL 陳述式或命令物件。 如需有關如何使用 Tableadapter 和命令進行查詢的詳細資訊，請參閱[使用 Tableadapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)。  
  
## <a name="executing-sql-statements-that-return-no-values-using-a-tableadapter"></a>執行沒有傳回值使用 TableAdapter 的 SQL 陳述式  
 此範例示範如何建立 TableAdapter 查詢 using[編輯 TableAdapters](../data-tools/editing-tableadapters.md)，然後宣告 TableAdapter 的執行個體及執行查詢的方式提供資訊。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-an-sql-statement-that-returns-no-value-using-a-tableadapter"></a>若要建立 SQL 陳述式未傳回值使用 TableAdapter  
  
1.  開啟中的資料集**Dataset 設計工具**。 如需詳細資訊，請參閱 <<c0> [ 如何： 以 Dataset 設計工具中開啟資料集](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。  
  
2.  如果您還沒有一個建立的 TableAdapter。 如需有關如何建立 Tableadapter 的詳細資訊，請參閱 <<c0> [ 建立和設定 Tableadapter](../data-tools/create-and-configure-tableadapters.md)。  
  
3.  如果您已經在您使用 SQL 陳述式未傳回值的 TableAdapter 上查詢，然後跳至下一個程序，「 宣告 TableAdapter 的執行個體，並執行查詢。 」 否則，請繼續進行步驟 4，以建立新的查詢未傳回值。  
  
4.  以滑鼠右鍵按一下您想要的 TableAdapter，並加入查詢中使用的捷徑功能表。  
  
     **TableAdapter 查詢組態精靈**隨即開啟。  
  
5.  保留預設值**使用 SQL 陳述式**，然後按一下**下一步**。  
  
6.  選擇**更新**，**插入**或是**刪除**選項，然後再按一下**下一步**。  
  
7.  輸入您的 SQL 陳述式，或使用**查詢產生器**來協助您建立一個，然後按一下**下一步**。  
  
8.  提供查詢名稱。  
  
9. 完成精靈。將查詢加入至 TableAdapter。  
  
10. 建置您的專案。  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>若要宣告 TableAdapter 的執行個體，並執行查詢  
  
1.  宣告 TableAdapter，其中包含您想要執行的查詢執行的個體。  
  
    -   若要建立使用設計階段工具的執行個體，拖曳您想從 TableAdapter**工具箱**。 (在專案中的元件現在都會出現在**工具箱**符合您的專案名稱的標題之下。)如果未出現在 TableAdapter**工具箱**，則您可能需要建置您的專案。  
  
         -或-  
  
    -   若要在程式碼中建立執行個體，取代下列程式碼的名稱與您<xref:System.Data.DataSet>和 TableAdapter。  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Tableadapter 實際上不會在其相關聯的資料集類別。 每個資料集有它自己的命名空間中的 TableAdapters 對應集合。 例如，如果您擁有名為資料集`SalesDataSet`，會有`SalesDataSetTableAdapters`包含其 TableAdapters 的命名空間。  
  
2.  呼叫您的查詢，如程式碼中呼叫其他方法一樣。 您的查詢是 TableAdapter 上的方法。 下列程式碼取代為 TableAdapter 和查詢的名稱。 您也需要在您的查詢所需的任何參數中傳遞。 如果您不確定，如果您的查詢需要參數，或哪些參數，它需要，然後檢查有無 IntelliSense 的查詢所需的簽章。 根據查詢是否會接受參數與否，程式碼看起來會類似下列範例的其中一項：  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     我們將視為未傳回任何值的查詢實際上會傳回值，包含查詢所影響的資料列數目的整數。 若要宣告 TableAdapter 的執行個體，並執行查詢的完整程式碼看起來應該如下所示：  
  
     [!code-csharp[VbRaddataFillingAndExecuting#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#11)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#11)]  
  
## <a name="executing-sql-statements-that-return-no-value-using-a-command-object"></a>執行 SQL 陳述式不傳回值使用的 Command 物件  
 下列範例示範如何建立命令，以及執行 SQL 陳述式未傳回值。 如需設定和取得命令的參數值的資訊，請參閱[如何： 設定和取得命令物件的參數](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)。  
  
 這個範例會使用<xref:System.Data.SqlClient.SqlCommand>物件，並需要：  
  
-   若要參考<xref:System>， <xref:System.Data>，和<xref:System.Xml>命名空間。  
  
-   資料連接名為`SqlConnection1`。  
  
-   一個名為資料表`Customers`在資料來源，`SqlConnection1`會連線到。 （否則您需要有效的 SQL 陳述式為資料來源）。  
  
#### <a name="to-execute-an-sql-statement-that-returns-no-value-using-a-datacommand"></a>若要執行不傳回值使用需要的 SQL 陳述式  
  
-   將下列程式碼新增至您想要執行的 SQL 陳述式的方法。 呼叫`ExecuteNonQuery`方法，不傳回值的命令 (例如<xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>)。  
  
     [!code-csharp[VbRaddataFillingAndExecuting#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#12)]
     [!code-vb[VbRaddataFillingAndExecuting#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#12)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 應用程式需要存取資料庫，並執行 SQL 陳述式的權限。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [如何： 建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)   
 [如何： 編輯 TableAdapter 查詢](../data-tools/how-to-edit-tableadapter-queries.md)   
 [如何： 使用資料填入資料集](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [使用 Tableadapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [如何： 設定及取得命令物件的參數](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)