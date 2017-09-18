---
title: "將資料填入資料集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "資料 [Visual Studio], 資料集"
  - "資料 [Visual Studio], 擷取"
  - "資料擷取"
  - "資料集 [Visual Basic]"
  - "資料集 [Visual Basic], 填滿"
  - "資料集 [Visual Basic], 載入資料"
  - "擷取資料"
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 32
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將資料填入資料集
TableAdapter 是用來執行 Transact\-SQL 查詢及填入資料集的典型 Visual Studio 機制。  
  
 您可以使用 TableAdapter 或命令物件 \(例如 <xref:System.Data.SqlClient.SqlCommand>\)，對資料來源執行 SQL 陳述式或預存程序。  若要將資料載入以 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 設計工具所建立的資料集，請使用 TableAdapter。  若要將資料載入以程式設計方式建立的資料集，則請使用資料配接器。  如果應用程式不使用資料集，請使用命令物件，直接對資料庫執行 SQL 陳述式或預存程序。  
  
 下列主題提供有關在 Visual Studio 中以資料填入資料集的詳細資訊：  
  
|主題|描述|  
|--------|--------|  
|[如何：以資料填入資料集](../data-tools/how-to-fill-a-dataset-with-data.md)|詳細說明如何使用 TableAdapter 和 DataAdapter 將資料載入資料集。|  
|[如何：建立及執行傳回資料列的 SQL 陳述式](../Topic/How%20to:%20Create%20and%20Execute%20an%20SQL%20Statement%20that%20Returns%20Rows.md)|詳細說明如何使用 TableAdapter 查詢和命令物件，建立及執行傳回資料列的 SQL 陳述式。|  
|[如何：建立及執行傳回單一值的 SQL 陳述式](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value.md)|詳細說明如何使用 TableAdapter 查詢和命令物件，建立及執行傳回單一值的 SQL 陳述式。|  
|[如何：建立及執行未傳回值的 SQL 陳述式](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-no-value.md)|詳細說明如何使用 TableAdapter 查詢和命令物件，建立及執行不傳回值的 SQL 陳述式。|  
|[如何：執行傳回資料列的預存程序](../Topic/How%20to:%20Execute%20a%20Stored%20Procedure%20that%20Returns%20Rows.md)|詳細說明如何使用 TableAdapter 查詢和命令物件，執行傳回資料列的預存程序。|  
|[如何：執行傳回單一值的預存程序](../data-tools/how-to-execute-a-stored-procedure-that-returns-a-single-value.md)|詳細說明如何使用 TableAdapter 查詢和命令物件，執行傳回單一值的預存程序。|  
|[如何：執行未傳回值的預存程序](../data-tools/how-to-execute-a-stored-procedure-that-returns-no-value.md)|詳細說明如何使用 TableAdapter 查詢和命令物件，執行不傳回值的預存程序。|  
|[如何：設定及取得命令物件的參數](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)|詳細說明如何指派值給查詢和預存程序中的參數，以及讀取執行命令後傳回的參數值。|  
|[逐步解說：以資料填入資料集](../Topic/Walkthrough:%20Filling%20a%20Dataset%20with%20Data.md)|提供建立資料集以及將資料庫的資料填入其中的細節。|  
|[逐步解說：將 XML 資料讀入資料集](../data-tools/read-xml-data-into-a-dataset.md)|詳細說明如何建立 Windows 應用程式，以便將 XML 資料載入資料集，然後在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示資料集。|  
  
## 填入資料集  
 如果您使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 設計階段工具 \(例如 [Dataset 設計工具](../data-tools/creating-and-editing-typed-datasets.md)或[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)\) 建立資料集，則要使用 TableAdapter 來填入此資料集。  TableAdapter 會執行 SQL 陳述式或預存程序。  
  
 如果您在不使用設計階段工具的情況下建立資料集，則必須使用資料配接器來填入及更新資料   \(TableAdapter 在 [.NET Framework 4.6 和 4.5](../Topic/.NET%20Framework%204.6%20and%204.5.md) 中並不是實際的類別，所以不適用於未使用設計階段工具所建立的資料集\)。  如需以 TableAdapter 或資料配接器將資料載入資料集的詳細資訊，請參閱 [如何：以資料填入資料集](../data-tools/how-to-fill-a-dataset-with-data.md)。  
  
## TableAdapter 查詢  
 您可以執行 TableAdapter 查詢，將資料填入資料集 \(更精確地說，將資料載入組成資料集的 DataTable\)。  使用 \[**DataSet 設計工具**\] 中的 [TableAdapter 查詢組態精靈](../data-tools/editing-tableadapters.md)建立 TableAdapter 查詢。  TableAdapter 查詢在 TableAdapter 中顯示為具名方法，透過呼叫 TableAdapter 方法予以執行。  如需建立和執行 TableAdapter 查詢的詳細資訊，請參閱下列頁面：  
  
-   [如何：建立及執行傳回資料列的 SQL 陳述式](../Topic/How%20to:%20Create%20and%20Execute%20an%20SQL%20Statement%20that%20Returns%20Rows.md)  
  
-   [如何：建立及執行傳回單一值的 SQL 陳述式](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value.md)  
  
-   [如何：建立及執行未傳回值的 SQL 陳述式](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-no-value.md)  
  
-   [如何：執行傳回資料列的預存程序](../Topic/How%20to:%20Execute%20a%20Stored%20Procedure%20that%20Returns%20Rows.md)  
  
-   [如何：執行傳回單一值的預存程序](../data-tools/how-to-execute-a-stored-procedure-that-returns-a-single-value.md)  
  
-   [如何：執行未傳回值的預存程序](../data-tools/how-to-execute-a-stored-procedure-that-returns-no-value.md)  
  
## 命令物件  
 命令物件讓您能夠直接對資料庫執行 SQL 陳述式和預存程序，而不需要 <xref:System.Data.DataSet>、TableAdapter 或 <xref:System.Data.Common.DataAdapter> \(*命令物件* \(Command Object\) 一詞指的是應用程式所使用的 .NET Framework Data Provider 的特定命令。  例如，如果您的應用程式使用 .NET Framework Data Provider for SQL Server，則命令物件會是 <xref:System.Data.SqlClient.SqlCommand>\)。  
  
 將資料命令的 `CommandType` 屬性設為其中一個 <xref:System.Data.IDbCommand.CommandType%2A> 列舉值，設定命令使用 SQL 陳述式或預存程序查詢資料。  若命令將要執行 SQL 陳述式，請將 `CommandType` 設為 <xref:System.Data.CommandType>；若執行預存程序，則將它設為 <xref:System.Data.CommandType>。  然後將 `CommandText` 屬性設為 SQL 陳述式或預存程序名稱。  之後，可以呼叫資料命令的其中一個執行方法 \(`ExecuteReader`、`ExecuteScalar`、`ExecuteNonQuery`\)，執行資料命令。  
  
 各版本的 [.NET Framework 資料提供者](../Topic/.NET%20Framework%20Data%20Providers.md)都會提供適合特定資料庫的命令物件。  
  
 透過資料命令的使用，您可在應用程式中進行下列作業：  
  
-   執行 Select 命令，傳回您可直接讀取的結果，而非將其載入資料集。  若要讀取結果，請使用資料讀取器 \(<xref:System.Data.OleDb.OleDbDataReader>、<xref:System.Data.SqlClient.SqlDataReader>、<xref:System.Data.Odbc.OdbcDataReader> 或 <xref:System.Data.OracleClient.OracleDataReader> 物件\)，其運作方式類似唯讀、順向游標，您可以繫結控制項給它。  這對於減少記憶體用量和迅速載入唯讀資料是相當有用的做法。  
  
-   執行資料庫定義語言 \(DDL\) 命令，以建立、編輯和移除資料表、預存程序和其他的資料庫結構   \(當然，您必須擁有執行這些動作的使用權限\)。  
  
-   執行命令以取得資料庫目錄資訊。  
  
-   執行動態 SQL 命令以更新、插入或刪除資料錄，而不是在更新資料集資料表後，再將變更部分複製到資料庫。  
  
-   執行可傳回純量值 \(也就是單一值\) 的命令，例如彙總函式 \(SUM、COUNT、AVG 等\) 的結果。  
  
-   執行命令，從 SQL Server 資料庫 \(7.0 或更新的版本\) 以 XML 格式傳回資料。  典型的用途如：執行查詢並以 XML 格式取回資料，對其套用 XSLT 轉換以將資料轉換成 HTML，再將結果傳送至瀏覽器。  
  
 命令的屬性包含針對資料庫執行命令時所需的一切資訊。  它們包括：  
  
-   **連接**：資料命令參考至一特定的連接，以便與資料庫通訊。  
  
-   **命令的名稱或文字**：命令包含所要執行 SQL 陳述式中實際的文字，或者是預存程序的名稱。  
  
-   **參數**：命令可能會要求同時傳遞參數值 \(輸入參數\)。  命令所傳回的值，也可能是以傳回值或輸出參數值的格式。  每個命令都有一參數集合，可個別設定或讀取以傳遞或取得值。  如需詳細資訊，請參閱 [如何：設定及取得命令物件的參數](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)。  
  
 使用適用於所要取回結果的方法，執行命令。  例如，如果您要取回資料列，必須呼叫命令的 `ExecuteReader` 方法，將資料錄傳回資料讀取器。  如果您要執行 UPDATE、INSERT 或 DELETE 命令，請呼叫命令的 `ExecuteNonQuery` 方法，它將傳回指出受影響之資料列數目的值。  如果您要執行彙總函式 \(例如傳回客戶訂單數\)，則呼叫 `ExecuteScalar` 方法。  
  
### 多重結果集  
 命令物件通常用來傳回單一資料表 \(一組資料列\)。  然而命令也可以執行傳回多重結果集的程序。  這可能出現於幾種情況。  其一是命令參考傳回多重結果集的預存程序。  或者，命令可包含兩個 \(或更多\) 陳述式或預存程序的名稱。  這種情況下，陳述式或程序會依序執行，而且可藉由單一呼叫傳回多重結果集。  
  
 如果為某一命令指定多個陳述式或程序，則它們必須屬於同一資料型別。  例如，您可執行連續的 SQL 陳述式或連續的預存程序，  但不能在同一命令中混用預存程序呼叫和 SQL 陳述式。  如需詳細資訊，請參閱[使用 DataReader 擷取資料](../Topic/Retrieving%20Data%20Using%20a%20DataReader.md)。  
  
> [!NOTE]
>  對於 Oracle 而言，.NET Framework Data Provider for Oracle 不支援批次處理的 SQL 陳述式。  然而，卻能讓您使用多個 REF CURSOR 輸出參數來填入資料集，並分別置於個別的資料表中。  必須定義參數，將其標示為輸出參數，並將其指示為 REF CURSOR 資料型別。  請注意，將 <xref:System.Data.OracleClient.OracleDataAdapter> 物件從 REF CURSOR 參數填入到預存程序時，將無法使用 `Update` 方法，因為當執行 SQL 陳述式時，Oracle 並不會提供決定資料表名稱和資料行名稱所需的資訊。  
  
## 安全性  
 使用 `CommandType` 屬性設為 <xref:System.Data.CommandType> 的資料命令時，請先仔細檢查用戶端傳送出來的資訊，然後再將這些資訊傳遞至資料庫。  惡意使用者會嘗試傳送 \(插入\) 修改過或額外的 SQL 陳述式 \(Statement\)，以獲取未經授權的存取權，或損壞資料庫。  在將使用者輸入傳輸到資料庫前，一定要確認資訊是有效的。  最好的做法是盡可能使用參數型查詢或預存程序。  
  
## 請參閱  
 [Visual Studio 資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)   
 [用來在 Visual Studio 中使用資料來源的工具](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)