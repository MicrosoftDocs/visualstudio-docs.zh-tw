---
title: CA3005：檢閱程式碼是否有 LDAP 插入式攻擊弱點
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
ms.openlocfilehash: 10b9091df08368674511b770158ea47c247aade7
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841366"
---
# <a name="ca3005-review-code-for-ldap-injection-vulnerabilities"></a>CA3005：檢閱程式碼是否有 LDAP 插入式攻擊弱點

|||
|-|-|
|TypeName|ReviewCodeForLdapInjectionVulnerabilities|
|CheckId|CA3005|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

可能不受信任的 HTTP 要求輸入到達的 LDAP 陳述式。

## <a name="rule-description"></a>規則描述

當使用不受信任的輸入，留意的輕量型目錄存取通訊協定 (LDAP) 資料隱碼攻擊。 攻擊者可以針對資訊的目錄執行惡意的 LDAP 陳述式。 使用使用者輸入來建構動態的 LDAP 陳述式，來存取目錄服務的應用程式會特別容易受到攻擊。

此規則會嘗試尋找 HTTP 要求到達的 LDAP 陳述式中的輸入。

> [!NOTE]
> 此規則無法追蹤多個組件的資料。 比方說，如果一個組件會讀取 HTTP 要求輸入，並再將它傳遞給另一個執行 LDAP 陳述式的組件，此規則將不會產生警告。

> [!NOTE]
> 沒有可設定的限制，深度此規則會分析資料流不同的方法呼叫。 請參閱[分析器組態](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis)如何 EditorConfig 檔案中設定限制。

## <a name="how-to-fix-violations"></a>如何修正違規

LDAP 陳述式的使用者控制部分，請考慮的其中一個：
- 允許安全清單的非特殊字元。
- 不允許特殊字元
- 逸出特殊字元。

請參閱[OWASP 的 LDAP 插入式攻擊防護功能提要](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/LDAP_Injection_Prevention_Cheat_Sheet.md)如需詳細指引。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您知道輸入已驗證或逸出為安全時，就可以隱藏這個警告。

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System;
using System.DirectoryServices;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userName = Request.Params["user"];
        string filter = "(uid=" + userName + ")";  // searching for the user entry

        // In this example, if we send the * character in the user parameter which will
        // result in the filter variable in the code to be initialized with (uid=*).
        // The resulting LDAP statement will make the server return any object that
        // contains a uid attribute.
        DirectorySearcher searcher = new DirectorySearcher(filter);
        SearchResultCollection results = searcher.FindAll();

        // Iterate through each SearchResult in the SearchResultCollection.
        foreach (SearchResult searchResult in results)
        {
            // ...
        }
    }
}
```

```vb
Imports System
Imports System.DirectoryServices

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(send As Object, e As EventArgs)
        Dim userName As String = Me.Request.Params(""user"")
        Dim filter As String = ""(uid="" + userName + "")""    ' searching for the user entry

        ' In this example, if we send the * character in the user parameter which will
        ' result in the filter variable in the code to be initialized with (uid=*).
        ' The resulting LDAP statement will make the server return any object that
        ' contains a uid attribute.
        Dim searcher As DirectorySearcher = new DirectorySearcher(filter)
        Dim results As SearchResultCollection = searcher.FindAll()

        ' Iterate through each SearchResult in the SearchResultCollection.
        For Each searchResult As SearchResult in results
            ' ...
        Next searchResult
    End Sub
End Class
```
