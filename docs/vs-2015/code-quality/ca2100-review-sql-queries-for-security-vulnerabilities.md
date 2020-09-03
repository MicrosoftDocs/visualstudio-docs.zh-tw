---
title: CA2100 必須：審查 SQL 查詢中的安全性弱點 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 797c071cdc74c36afeece304bfa4c708d7bf7147
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521208"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100:必須檢閱 SQL 查詢中是否有安全性弱點
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|類別|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法 <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> 會使用從字串引數建立至方法的字串，來設定屬性。

## <a name="rule-description"></a>規則描述
 這項規則假設字串引數包含使用者輸入。 從使用者輸入所建置的 SQL 命令字串很容易遭到 SQL 插入 (SQL Injection) 攻擊。 在 SQL 插入式攻擊中，惡意使用者所提供的輸入會改變查詢的設計，以嘗試損毀或獲得未授權的基礎資料庫存取權。 一般技巧包括插入單引號或單引號，也就是 SQL 常值字串分隔符號;兩個虛線，表示 SQL 批註;和分號，表示後面接著新的命令。 如果使用者輸入必須是查詢的一部分，請使用下列其中一項（以有效性順序列出）來降低攻擊的風險。

- 使用預存程序。

- 使用參數化命令字串。

- 在您建立命令字串之前，請先驗證型別和內容的使用者輸入。

  下列 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 類型會執行 <xref:System.Data.IDbCommand.CommandText%2A> 屬性，或提供使用字串引數來設定屬性的函式。

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> 和 <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> 和 <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> 和 <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- [System.data.sqlserverce. SqlCeCommand] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) 和 [System.data.sqlserverce. SqlCeDataAdapter] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> 和 <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

  請注意，當使用型別的 ToString 方法以明確或隱含方式來建立查詢字串時，會違反此規則。 以下是一個範例。

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 違反規則是因為惡意使用者可以覆寫 ToString ( # A1 方法。

 隱含使用 ToString 時，也會違反此規則。

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用參數化查詢。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果命令文字未包含任何使用者輸入，就可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的方法， `UnsafeQuery` 以及 `SaferQuery` 使用參數化命令字串滿足規則的方法。

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>另請參閱
 [安全性概觀](https://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)
