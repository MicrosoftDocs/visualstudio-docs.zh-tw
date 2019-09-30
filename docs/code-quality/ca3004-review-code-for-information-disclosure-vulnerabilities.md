---
title: CA3004：檢閱程式碼是否有資訊洩漏弱點
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
ms.openlocfilehash: 4965c9df3c2256511b8e44de8d388a9155d0d8f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237382"
---
# <a name="ca3004-review-code-for-information-disclosure-vulnerabilities"></a>CA3004：檢閱程式碼是否有資訊洩漏弱點

|||
|-|-|
|TypeName|ReviewCodeForInformationDisclosureVulnerabilities|
|CheckId|CA3004|
|分類|Microsoft.Security|
|重大變更|不中斷|

## <a name="cause"></a>原因

例外狀況的訊息、堆疊追蹤或字串表示達到 web 輸出。

## <a name="rule-description"></a>規則描述

公開例外狀況資訊可讓攻擊者深入瞭解應用程式的內部，以協助攻擊者找出其他弱點來入侵。

此規則會嘗試尋找要輸出至 HTTP 回應的例外狀況訊息、堆疊追蹤或字串表示。

> [!NOTE]
> 此規則無法跨元件追蹤資料。 例如，如果某個元件攔截例外狀況，然後將它傳遞給另一個輸出例外狀況的元件，此規則就不會產生警告。

> [!NOTE]
> 此規則會在方法呼叫中分析資料流的深度有一個可設定的限制。 如需如何在 EditorConfig 檔中設定限制的詳細說明，請參閱[分析器](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis)設定。

## <a name="how-to-fix-violations"></a>如何修正違規

不要將例外狀況資訊輸出至 HTTP 回應。 相反地，請提供一般錯誤訊息。 如需詳細指引，請參閱[OWASP 的錯誤處理頁面](https://www.owasp.org/index.php/Error_Handling)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您知道 web 輸出是在應用程式的信任界限內，而且永遠不會公開于外，就可以隱藏這個警告。 這種情況很罕見。 請注意，應用程式的信任界限和資料流程可能會隨著時間而改變。

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