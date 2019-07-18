---
title: CA3008：檢閱程式碼是否有 XPath 插入式攻擊弱點
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
ms.openlocfilehash: 5a4b80b8ede1ab2b8d858ed7378f318f2eebe5fa
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841529"
---
# <a name="ca3008-review-code-for-xpath-injection-vulnerabilities"></a>CA3008：檢閱程式碼是否有 XPath 插入式攻擊弱點

|||
|-|-|
|TypeName|ReviewCodeForXPathInjectionVulnerabilities|
|CheckId|CA3008|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

可能不受信任的 HTTP 要求輸入達到 XPath 查詢。

## <a name="rule-description"></a>規則描述

當使用不受信任的輸入，留意 XPath 資料隱碼攻擊。 建構使用不受信任的輸入 XPath 查詢，可能會讓攻擊者惡意地操作傳回非預期的結果，查詢，並可能是公開的查詢的 XML 內容。

此規則會嘗試尋找 HTTP 要求到達的 XPath 運算式中的輸入。

> [!NOTE]
> 此規則無法追蹤多個組件的資料。 比方說，如果一個組件會讀取 HTTP 要求輸入，然後將它傳遞給另一個組件會執行 XPath 查詢，此規則將不會產生警告。

> [!NOTE]
> 沒有可設定的限制，深度此規則會分析資料流不同的方法呼叫。 請參閱[分析器組態](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis)如何 EditorConfig 檔案中設定限制。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正 XPath 資料隱碼漏洞的一些方法包括：

- 不會建構從使用者輸入的 XPath 查詢。
- 驗證輸入只包含一組安全的字元。
- 逸出引號。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您知道您已驗證的輸入，為了安全起見，就可以隱藏這個警告。

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System;
using System.Xml.XPath;

public partial class WebForm : System.Web.UI.Page
{
    public XPathNavigator AuthorizedOperations { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string operation = Request.Form["operation"];

        // If an attacker uses this for input:
        //     ' or 'a' = 'a
        // Then the XPath query will be:
        //     authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        // and it will return any authorizedOperation node.
        XPathNavigator node = AuthorizedOperations.SelectSingleNode(
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']");
    }
}
```

```vb
Imports System
Imports System.Xml.XPath

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Public Property AuthorizedOperations As XPathNavigator

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim operation As String = Me.Request.Form("operation")

        ' If an attacker uses this for input:
        '     ' or 'a' = 'a
        ' Then the XPath query will be:
        '      authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        ' and it will return any authorizedOperation node.
        Dim node As XPathNavigator = AuthorizedOperations.SelectSingleNode( _
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']")
    End Sub
End Class
```
