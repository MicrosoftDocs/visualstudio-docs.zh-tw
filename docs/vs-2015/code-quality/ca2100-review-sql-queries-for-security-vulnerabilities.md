---
title: CA2100： 檢閱 SQL 查詢是否有安全性弱點 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0c269fe38a50a6d36003bffd65a7884d48c3473a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588306"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100：必須檢視 SQL 查詢中是否有安全性弱點
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA2100： 檢閱 SQL 查詢是否有安全性弱點](https://docs.microsoft.com/visualstudio/code-quality/ca2100-review-sql-queries-for-security-vulnerabilities)。

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|分類|Microsoft.Security|
|中斷變更|非重大|

## <a name="cause"></a>原因
 方法會設定<xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName>所使用的字串，內建字串引數之方法的屬性。

## <a name="rule-description"></a>規則描述
 這項規則假設字串引數包含使用者輸入。 從使用者輸入所建置的 SQL 命令字串很容易遭到 SQL 插入 (SQL Injection) 攻擊。 在 SQL 資料隱碼攻擊，惡意使用者所提供的改變查詢的設計嘗試損毀或未經授權存取基礎資料庫中的輸入。 典型的技術包括資料隱碼攻擊的單引號或縮寫符號，也就是 SQL 常值字串分隔符號中;兩個連字號，這表示 SQL 註解;和分號，這表示，新的命令如下所示。 如果使用者輸入必須是查詢的一部份，下列程式碼，使用其中一個列出的有效性，為了降低攻擊風險。

-   使用預存程序。

-   使用參數化的命令的字串。

-   建置命令字串之前，請驗證使用者輸入的類型和內容。

 下列[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]型別會實作<xref:System.Data.IDbCommand.CommandText%2A>屬性或建構函式，使用字串引數設定的屬性。

-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> 和 <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> 和 <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> 和 <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

-   [System.Data.SqlServerCe.SqlCeCommand](<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) 和 [System.Data.SqlServerCe.SqlCeDataAdapter] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> 和 <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

 請注意，在明確或隱含使用 ToString 方法的型別時，違反此規則來建構查詢字串。 下列為範例。

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 因為惡意使用者可以覆寫 tostring （） 方法違反此規則。

 也會隱含地使用 ToString 時，會違反規則。

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用參數化的查詢。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，如果命令文字不包含任何使用者輸入。

## <a name="example"></a>範例
 下列範例示範的方法中， `UnsafeQuery`，，違反規則和方法， `SaferQuery`，使用參數化的命令字串符合規則。

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>另請參閱
 [安全性概觀](http://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)



