---
title: CA3003:檢閱程式碼的檔案路徑資料隱碼攻擊弱點
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
ms.openlocfilehash: c20d3efb9ea84a7e8bb22288303313ef44b2b795
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018483"
---
# <a name="ca3003-review-code-for-file-path-injection-vulnerabilities"></a>CA3003:檢閱程式碼的檔案路徑資料隱碼攻擊弱點

|||
|-|-|
|TypeName|ReviewCodeForFilePathInjectionVulnerabilities|
|CheckId|CA3003|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

可能不受信任的 HTTP 要求輸入到達檔案作業的路徑。

## <a name="rule-description"></a>規則描述

當使用不受信任的輸入，從 web 要求，留意指定檔案的路徑時，使用使用者控制的輸入。 攻擊者可以讀取的非預期的檔案，導致資訊洩漏的機密資料。 或者，攻擊者可能會將寫入非預期的檔案，導致未經授權的機密資料修改，或危及伺服器的安全性。 常見的攻擊者技術[路徑周遊](https://www.owasp.org/index.php/Path_Traversal)存取想要的目錄外部的檔案。

此規則會嘗試尋找到達的路徑中檔案作業的 HTTP 要求中的輸入。

> [!NOTE]
> 此規則無法追蹤多個組件的資料。 比方說，如果一個組件會讀取 HTTP 要求輸入，然後將它傳遞給另一個組件寫入檔案，此規則將不會產生警告。

> [!NOTE]
> 沒有可設定的限制，深度此規則會分析資料流不同的方法呼叫。 請參閱[分析器組態](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis)如何設定中的限制`.editorconfig`檔案。

## <a name="how-to-fix-violations"></a>如何修正違規

- 可能的話，請限制根據使用者輸入至明確已知的安全清單的檔案路徑。  例如，如果您的應用程式只需要存取 「 red.txt"、"green.txt 」 或 「 blue.txt"，只允許這些值。
- 檢查未受信任的檔案名稱，並驗證格式正確的名稱。
- 指定路徑時，請使用完整路徑名稱。
- 避免潛在的危險的建構，例如路徑環境變數。
- 只會接收的長檔名和驗證完整名稱，如果使用者送出的簡短名稱。
- 限制終端使用者輸入有效的字元。
- 拒絕超出 MAX_PATH 長度的名稱。
- 而不進行解譯，也就是處理檔名。
- 判斷是否檔名表示檔案或裝置。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您已在上一節中所述，驗證輸入，，就可以隱藏這個警告。

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userInput = Request.Params["UserInput"];
        // Assume the following directory structure:
        //   wwwroot\currentWebDirectory\user1.txt
        //   wwwroot\currentWebDirectory\user2.txt
        //   wwwroot\secret\allsecrets.txt
        // There is nothing wrong if the user inputs:
        //   user1.txt
        // However, if the user input is: 
        //   ..\secret\allsecrets.txt
        // Then an attacker can now see all the secrets.

        // Avoid this:
        using (File.Open(userInput, FileMode.Open))
        {
            // Read a file with the name supplied by user
            // Input through request's query string and display 
            // The content to the webpage. 
        }
    }
}
```

```vb
Imports System
Imports System.IO

Partial Public Class WebForm 
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim userInput As String = Me.Request.Params("UserInput")
        ' Assume the following directory structure:
        '   wwwroot\currentWebDirectory\user1.txt
        '   wwwroot\currentWebDirectory\user2.txt
        '   wwwroot\secret\allsecrets.txt
        ' There is nothing wrong if the user inputs:
        '   user1.txt
        ' However, if the user input is: 
        '   ..\secret\allsecrets.txt
        ' Then an attacker can now see all the secrets.

        ' Avoid this:
        Using File.Open(userInput, FileMode.Open)
            ' Read a file with the name supplied by user
            ' Input through request's query string and display 
            ' The content to the webpage. 
        End Using
    End Sub
End Class
```
