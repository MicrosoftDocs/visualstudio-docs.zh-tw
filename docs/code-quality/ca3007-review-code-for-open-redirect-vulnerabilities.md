---
title: CA3007：檢閱程式碼是否有開放式重新導向弱點
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
ms.openlocfilehash: dbafb6c05a3dba72d1614d6a955e20030a50c6ea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541164"
---
# <a name="ca3007-review-code-for-open-redirect-vulnerabilities"></a>CA3007：檢閱程式碼是否有開放式重新導向弱點

|||
|-|-|
|TypeName|ReviewCodeForOpenRedirectVulnerabilities|
|CheckId|CA3007|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

可能不受信任的 HTTP 要求輸入連至的 HTTP 回應重新導向。

## <a name="rule-description"></a>規則描述

當使用不受信任的輸入，留意開啟重新導向弱點。 攻擊者可以開啟重新導向弱點的合法的 URL，但重新導向至網路釣魚或其他惡意的網頁遲疑不前訪客使用您的網站。

此規則會嘗試尋找達到 HTTP 重新導向 URL 的 HTTP 要求中的輸入。

> [!NOTE]
> 此規則無法追蹤多個組件的資料。 比方說，如果一個組件會讀取 HTTP 要求輸入，並再將它傳遞至回應的 HTTP 重新導向的另一個組件，此規則將不會產生警告。

> [!NOTE]
> 沒有可設定的限制，深度此規則會分析資料流不同的方法呼叫。 請參閱[分析器組態](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis)如何設定中的限制`.editorconfig`檔案。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正開啟重新導向弱點的一些方法包括：

- 不允許使用者起始重新導向。
- 不允許使用者重新導向情節中指定 URL 的任何一部分。
- 限制 重新導向至預先定義 「 允許清單 」 的 Url。
- 驗證重新導向 Url。
- 如果適用的話，請考慮使用免責聲明頁面上，當使用者被重新導向遠離您的網站。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您知道您已驗證的輸入限制為預期的 Url，就可以隱藏這個警告。

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["url"];
        this.Response.Redirect(input);
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("url")
        Me.Response.Redirect(input)
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
        if (String.IsNullOrWhiteSpace(input))
        {
            this.Response.Redirect("https://example.org/login.html");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("in")
        If String.IsNullOrWhiteSpace(input) Then
            Me.Response.Redirect("https://example.org/login.html")
        End If
    End Sub
End Class
```
