---
title: CA3012:檢閱 regex 資料隱碼弱點的程式碼
ms.date: 04/03/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 114b44ec566554c81f5caf3b8ac474f9c5a75c07
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018481"
---
# <a name="ca3012-review-code-for-regex-injection-vulnerabilities"></a>CA3012:檢閱 regex 資料隱碼弱點的程式碼

|||
|-|-|
|TypeName|ReviewCodeForRegexInjectionVulnerabilities|
|CheckId|CA3012|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

可能不受信任的 HTTP 要求輸入達到規則運算式。

## <a name="rule-description"></a>規則描述

當使用不受信任的輸入，留意 regex 資料隱碼攻擊。 攻擊者可以使用 regex 資料隱碼攻擊，惡意修改規則運算式進行比對非預期的結果，regex，或將 regex 會耗用大量的 CPU，因而導致阻絕服務攻擊。

此規則會嘗試尋找達到規則運算式的 HTTP 要求中的輸入。

> [!NOTE]
> 此規則無法追蹤多個組件的資料。 例如，如果一個組件會讀取 HTTP 要求輸入，然後將它傳遞給另一個組件所建立的規則運算式這個規則將不會產生警告。

> [!NOTE]
> 沒有可設定的限制，深度此規則會分析資料流不同的方法呼叫。 請參閱[分析器組態](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis)如何設定中的限制`.editorconfig`檔案。

## <a name="how-to-fix-violations"></a>如何修正違規

預防 regex 插入式攻擊的一些風險降低方式包括：

- 一律使用[比對逾時](/dotnet/standard/base-types/best-practices#use-time-out-values)時使用規則運算式。
- 請避免使用根據使用者輸入的規則運算式。
- 使用者輸入的逸出特殊字元，藉由呼叫<xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=fullName>或另一種方法。
- 允許從使用者輸入的只有非特殊字元。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您知道您使用[比對逾時](/dotnet/standard/base-types/best-practices#use-time-out-values)和使用者的輸入是免費的特殊字元，可以隱藏這個警告。

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System;
using System.Text.RegularExpressions;

public partial class WebForm : System.Web.UI.Page
{
    public string SearchableText { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string findTerm = Request.Form["findTerm"];
        Match m = Regex.Match(SearchableText, "^term=" + findTerm);
    }
}
```

```vb
Imports System
Imports System.Text.RegularExpressions

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Public Property SearchableText As String

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim findTerm As String = Request.Form("findTerm")
        Dim m As Match = Regex.Match(SearchableText, "^term=" + findTerm)
    End Sub
End Class
```
