---
title: CA3002：檢閱程式碼是否有 XSS 弱點
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
ms.openlocfilehash: 383011e53b14ec2cc7dd7474cd050f05295a2a73
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841475"
---
# <a name="ca3002-review-code-for-xss-vulnerabilities"></a>CA3002：檢閱程式碼是否有 XSS 弱點

|||
|-|-|
|TypeName|ReviewCodeForXssVulnerabilities|
|CheckId|CA3002|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

可能不受信任的 HTTP 要求輸入連至原始的 HTML 輸出。

## <a name="rule-description"></a>規則描述

當使用不受信任的輸入，從 web 要求，留意跨網站指令碼 (XSS) 攻擊。 XSS 攻擊會將未受信任的輸入插入原始 HTML 輸出，讓攻擊者執行惡意指令碼或惡意修改在網頁中的內容。 典型的技巧會讓`<script>`輸入中的惡意程式碼的項目。 如需詳細資訊，請參閱 < [OWASP 的 XSS](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS))。

此規則會嘗試尋找達到原始 HTML 輸出的 HTTP 要求中的輸入。

> [!NOTE]
> 此規則無法追蹤多個組件的資料。 比方說，如果一個組件會讀取 HTTP 要求輸入，並再將它傳遞給輸出原始 HTML 的另一個組件，此規則將不會產生警告。

> [!NOTE]
> 沒有可設定的限制，深度此規則會分析資料流不同的方法呼叫。 請參閱[分析器組態](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis)如何 EditorConfig 檔案中設定限制。

## <a name="how-to-fix-violations"></a>如何修正違規

- 而不是輸出原始 HTML，使用方法或屬性的第一個 HTML 編碼輸入。
- HTML 編碼不受信任的資料，然後才會輸出原始 HTML。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏此規則的警告，如果：
- 您知道輸入已驗證對已知安全的一組字元不包含 HTML。
- 您知道資料是 HTML 編碼的方式，此規則偵測不到。

> [!NOTE]
> 此規則可能會誤判報告的一些方法或屬性的 HTML 編碼其輸入。

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Response.Write("<HTML>" + input + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")
        Me.Response.Write("<HTML>" + input + "</HTML>")
    End Sub
End Class
```

### <a name="solution"></a>方案

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];

        // Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Response.Write("<HTML>" + Server.HtmlEncode(input) + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")

        ' Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Me.Response.Write("<HTML>" + Me.Server.HtmlEncode(input) + "</HTML>")
    End Sub
End Class
```