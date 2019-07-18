---
title: CA3011：檢閱程式碼是否有 DLL 插入式攻擊弱點
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
ms.openlocfilehash: 4c9fbb4b8b11b0fce7d3e7530eef80af19b35b73
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841023"
---
# <a name="ca3011-review-code-for-dll-injection-vulnerabilities"></a>CA3011：檢閱程式碼是否有 DLL 插入式攻擊弱點

|||
|-|-|
|TypeName|ReviewCodeForDllInjectionVulnerabilities|
|CheckId|CA3011|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

可能不受信任的 HTTP 要求輸入達到方法，載入組件。

## <a name="rule-description"></a>規則描述

當使用不受信任的輸入，留意載入未受信任的程式碼。 如果您的 web 應用程式會載入未受信任的程式碼，攻擊者可以您的程序插入惡意的 Dll 並執行惡意程式碼。

此規則會嘗試尋找輸入 HTTP 要求，達到載入組件的方法。

> [!NOTE]
> 此規則無法追蹤多個組件的資料。 比方說，如果一個組件會讀取 HTTP 要求輸入，然後將它傳遞給另一個組件，載入組件，此規則將不會產生警告。

> [!NOTE]
> 沒有可設定的限制，深度此規則會分析資料流不同的方法呼叫。 請參閱[分析器組態](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis)如何 EditorConfig 檔案中設定限制。

## <a name="how-to-fix-violations"></a>如何修正違規

不要載入來自使用者輸入的不受信任的 Dll。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏這項規則的警告。

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System;
using System.Reflection;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] rawAssembly = Convert.FromBase64String(input);
        Assembly.Load(rawAssembly);
    }
}
```

```vb
Imports System
Imports System.Reflection

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim rawAssembly As Byte() = Convert.FromBase64String(input)
        Assembly.Load(rawAssembly)
    End Sub
End Class
```
