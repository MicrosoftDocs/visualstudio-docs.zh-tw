---
title: CA3006:檢閱程序命令插入式攻擊弱點的程式碼
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
ms.openlocfilehash: da161e611ca1d802c8da16370907029233bfd785
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018487"
---
# <a name="ca3006-review-code-for-process-command-injection-vulnerabilities"></a>CA3006:檢閱程序命令插入式攻擊弱點的程式碼

|||
|-|-|
|TypeName|ReviewCodeForProcessCommandInjectionVulnerabilities|
|CheckId|CA3006|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

可能不受信任的 HTTP 要求輸入達到處理命令。

## <a name="rule-description"></a>規則描述

當使用不受信任的輸入，留意命令插入式攻擊。 命令資料隱碼攻擊可以在基礎作業系統洩露的安全性和完整性，您的伺服器上執行惡意的命令。

此規則會嘗試尋找到達處理命令的 HTTP 要求中的輸入。

> [!NOTE]
> 此規則無法追蹤多個組件的資料。 比方說，如果一個組件會讀取 HTTP 要求輸入，並再將它傳遞給啟動的處理序的另一個組件，此規則將不會產生警告。

> [!NOTE]
> 沒有可設定的限制，深度此規則會分析資料流不同的方法呼叫。 請參閱[分析器組態](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis)如何設定中的限制`.editorconfig`檔案。

## <a name="how-to-fix-violations"></a>如何修正違規

- 可能的話，請避免啟動程序根據使用者輸入。
- 驗證輸入，針對已知的安全組字元的長度。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您知道輸入已驗證或逸出為安全，它可安全地隱藏這個警告。

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System;
using System.Diagnostics;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Process p = Process.Start(input);
    }
}
```

```vb
Imports System
Imports System.Diagnostics

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs as EventArgs)
        Dim input As String = Me.Request.Form("in")
        Dim p As Process = Process.Start(input)
    End Sub
End Class
```
