---
title: CA3004:檢閱資訊洩漏弱點的程式碼
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
ms.openlocfilehash: 82f763d9a6b1ec27975aa80054456a6bbbaeaa2b
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018482"
---
# <a name="ca3004-review-code-for-information-disclosure-vulnerabilities"></a>CA3004:檢閱資訊洩漏弱點的程式碼

|||
|-|-|
|TypeName|ReviewCodeForInformationDisclosureVulnerabilities|
|CheckId|CA3004|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

例外狀況的訊息、 堆疊追蹤或字串表示法會到達 web 輸出。

## <a name="rule-description"></a>規則描述

例外狀況資訊洩漏讓攻擊者深入了解您的應用程式，可協助攻擊者的內部資訊找到其他的弱點惡意探索。

此規則會嘗試尋找例外狀況訊息、 堆疊追蹤或要輸出至 HTTP 回應的字串表示。

> [!NOTE]
> 此規則無法追蹤多個組件的資料。 比方說，如果一個組件會攔截到例外狀況，並再將它傳遞給輸出例外狀況的另一個組件，此規則將不會產生警告。

> [!NOTE]
> 沒有可設定的限制，深度此規則會分析資料流不同的方法呼叫。 請參閱[分析器組態](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis)如何設定中的限制`.editorconfig`檔案。

## <a name="how-to-fix-violations"></a>如何修正違規

不會輸出至 HTTP 回應的例外狀況資訊。 相反地，提供一般錯誤訊息。 請參閱[OWASP 的錯誤處理頁面](https://www.owasp.org/index.php/Error_Handling)如需詳細指引。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您知道您的 web 輸出是您的應用程式信任界限內，而且永遠不會公開之外，可以隱藏這個警告。 這個狀況非常罕見。 請考量您的應用程式信任界限以及資料流可能會隨著時間改變。

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write(e.ToString());
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm 
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write(e.ToString())
        End Try
    End Sub
End Class
```

### <a name="solution"></a>方案

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write("An error occurred. Please try again later.");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm 
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write("An error occurred. Please try again later.")
        End Try
    End Sub
End Class
```