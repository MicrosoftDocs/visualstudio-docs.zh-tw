---
title: CA3010：檢閱程式碼是否有 XAML 插入式攻擊弱點
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
ms.openlocfilehash: ea53f5e0cddf1dc6c6caf4c7fcfb79af52ce354e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103689"
---
# <a name="ca3010-review-code-for-xaml-injection-vulnerabilities"></a>CA3010：檢閱程式碼是否有 XAML 插入式攻擊弱點

|||
|-|-|
|TypeName|ReviewCodeForXamlInjectionVulnerabilities|
|CheckId|CA3010|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

可能不受信任的 HTTP 要求輸入達到<xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType>負載方法。

## <a name="rule-description"></a>規則描述

當使用不受信任的輸入，留意 XAML 資料隱碼攻擊。 XAML 是直接表示物件執行個體化和執行的標記語言。 這表示在 XAML 中建立的項目可以與系統資源 （例如，網路存取權和檔案系統 IO） 互動。 如果攻擊者可以控制的輸入<xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType>載入方法呼叫，則攻擊者可以執行程式碼。

此規則會嘗試尋找 HTTP 要求中達到的輸入<xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType>負載方法。

> [!NOTE]
> 此規則無法追蹤多個組件的資料。 例如，如果一個組件會讀取 HTTP 要求輸入，然後將它傳遞給另一個組件載入 XAML 此規則將不會產生警告。

> [!NOTE]
> 沒有可設定的限制，深度此規則會分析資料流不同的方法呼叫。 請參閱[分析器組態](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis)如何設定中的限制`.editorconfig`檔案。

## <a name="how-to-fix-violations"></a>如何修正違規

不要載入未受信任的 XAML。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏這項規則的警告。

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] bytes = Convert.FromBase64String(input);
        MemoryStream ms = new MemoryStream(bytes);
        System.Windows.Markup.XamlReader.Load(ms);
    }
}
```

```vb
Imports System
Imports System.IO

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim bytes As Byte() = Convert.FromBase64String(input)
        Dim ms As MemoryStream = New MemoryStream(bytes)
        System.Windows.Markup.XamlReader.Load(ms)
    End Sub
End Class
```
