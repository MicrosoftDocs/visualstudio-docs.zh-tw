---
title: CA3009：檢閱程式碼是否有 XML 插入式攻擊弱點
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
ms.openlocfilehash: 2f0b0ba39c8edee9b2b8df608b47a00e6353538f
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841073"
---
# <a name="ca3009-review-code-for-xml-injection-vulnerabilities"></a>CA3009：檢閱程式碼是否有 XML 插入式攻擊弱點

|||
|-|-|
|TypeName|ReviewCodeForXmlInjectionVulnerabilities|
|CheckId|CA3009|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

可能不受信任的 HTTP 要求輸入連至原始的 XML 輸出。

## <a name="rule-description"></a>規則描述

當使用不受信任的輸入，留意 XML 插入式攻擊。 攻擊者可以使用 XML 資料隱碼攻擊，將特殊字元插入 XML 文件，使得文件無效 XML。 或者，攻擊者可能遭到惡意插入他們所選擇的 XML 節點。

此規則會嘗試尋找達到原始資料的 XML 寫入 HTTP 要求中的輸入。

> [!NOTE]
> 此規則無法追蹤多個組件的資料。 例如，如果一個組件會讀取 HTTP 要求輸入，然後將它傳遞給寫入原始 XML 的另一個組件這項規則將不會產生警告。

> [!NOTE]
> 沒有可設定的限制，深度此規則會分析資料流不同的方法呼叫。 請參閱[分析器組態](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis)如何 EditorConfig 檔案中設定限制。

## <a name="how-to-fix-violations"></a>如何修正違規

不要撰寫原始 XML。 相反地，使用方法或屬性的 XML 編碼其輸入。

或者，XML 編碼的輸入，才會寫入未經處理的 XML。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏這項規則的警告。

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System;
using System.Xml;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        XmlDocument d = new XmlDocument();
        XmlElement root = d.CreateElement("root");
        d.AppendChild(root);

        XmlElement allowedUser = d.CreateElement("allowedUser");
        root.AppendChild(allowedUser);

        allowedUser.InnerXml = "alice";

        // If an attacker uses this for input:
        //     some text<allowedUser>oscar</allowedUser>
        // Then the XML document will be:
        //     <root>some text<allowedUser>oscar</allowedUser></root>
        root.InnerXml = input;
    }
}
```

```vb
Imports System
Imports System.Xml

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim d As XmlDocument = New XmlDocument()
        Dim root As XmlElement = d.CreateElement("root")
        d.AppendChild(root)

        Dim allowedUser As XmlElement = d.CreateElement("allowedUser")
        root.AppendChild(allowedUser)

        allowedUser.InnerXml = "alice"

        ' If an attacker uses this for input:
        '     some text<allowedUser>oscar</allowedUser>
        ' Then the XML document will be:
        '     <root>some text<allowedUser>oscar</allowedUser></root>
        root.InnerXml = input
    End Sub
End Class
```

### <a name="solution"></a>方案

```csharp
using System;
using System.Xml;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        XmlDocument d = new XmlDocument();
        XmlElement root = d.CreateElement("root");
        d.AppendChild(root);

        XmlElement allowedUser = d.CreateElement("allowedUser");
        root.AppendChild(allowedUser);

        allowedUser.InnerText = "alice";

        // If an attacker uses this for input:
        //     some text<allowedUser>oscar</allowedUser>
        // Then the XML document will be:
        //     <root>&lt;allowedUser&gt;oscar&lt;/allowedUser&gt;some text<allowedUser>alice</allowedUser></root>
        root.InnerText = input;
    }
}
```

```vb
Imports System
Imports System.Xml

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim d As XmlDocument = New XmlDocument()
        Dim root As XmlElement = d.CreateElement("root")
        d.AppendChild(root)

        Dim allowedUser As XmlElement = d.CreateElement("allowedUser")
        root.AppendChild(allowedUser)

        allowedUser.InnerText = "alice"

        ' If an attacker uses this for input:
        '     some text<allowedUser>oscar</allowedUser>
        ' Then the XML document will be:
        '     <root>&lt;allowedUser&gt;oscar&lt;/allowedUser&gt;some text<allowedUser>alice</allowedUser></root>
        root.InnerText = input
    End Sub
End Class
```
