---
title: "CA2100： 檢閱 SQL 查詢是否有安全性弱點 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e653f4b4d1cb350b936b4b8d906b43b3926b741e
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2017
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100：必須檢視 SQL 查詢中是否有安全性弱點
|||  
|-|-|  
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|  
|CheckId|CA2100|  
|分類|Microsoft.Security|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 方法會設定<xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName>屬性，方法是使用建置的字串引數之方法的字串。  
  
## <a name="rule-description"></a>規則描述  
 這項規則假設字串引數包含使用者輸入。 從使用者輸入所建置的 SQL 命令字串很容易遭到 SQL 插入 (SQL Injection) 攻擊。 在 SQL 資料隱碼攻擊中，惡意使用者所提供的輸入會改變查詢的設計嘗試損毀或未經授權存取基礎資料庫中。 典型的技術包括資料隱碼的單引號 （或單引號），這是 SQL 的常值字串分隔符號。兩個連字號，這表示 SQL 註解。和分號，這表示，新的命令如下所示。 如果使用者輸入必須是查詢的一部份，下列程式碼，使用其中一個的順序列出的有效性，以減少攻擊的風險。  
  
-   使用預存程序。  
  
-   使用參數化的命令字串。  
  
-   建置命令字串之前，請驗證使用者輸入的類型和內容。  
  
 下列[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]型別會實作<xref:System.Data.IDbCommand.CommandText%2A>屬性或建構函式，將屬性設定為字串引數。  
  
-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> 和 <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> 和 <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> 和 <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> 和 <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>  
  
 請注意，在明確或隱含使用 ToString 方法的型別時，違反這項規則來建構查詢字串。 下列為範例。  
  
```  
int x = 10;  
string query = "SELECT TOP " + x.ToString() + " FROM Table";  
```  
  
 因為惡意使用者可以覆寫 tostring （） 方法違反此規則。  
  
 違反規則，也會隱含地使用 ToString 時。  
  
```  
int x = 10;  
string query = String.Format("SELECT TOP {0} FROM Table", x);  
```  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，使用參數化的查詢。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，如果命令文字不包含任何使用者輸入。  
  
## <a name="example"></a>範例  
 下列範例會示範一種方法， `UnsafeQuery`，違反規則和方法， `SaferQuery`，使用參數化的命令字串符合規則。  
  
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [安全性概觀](/dotnet/framework/data/adonet/security-overview)