---
title: CA3003：檢閱程式碼是否有檔案路徑插入式攻擊弱點
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
ms.openlocfilehash: c9e43dcdf1e923cb7bc4a98b17fd0be71b7927eb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237404"
---
# <a name="ca3003-review-code-for-file-path-injection-vulnerabilities"></a>CA3003：檢閱程式碼是否有檔案路徑插入式攻擊弱點

|||
|-|-|
|TypeName|ReviewCodeForFilePathInjectionVulnerabilities|
|CheckId|CA3003|
|分類|Microsoft.Security|
|重大變更|不中斷|

## <a name="cause"></a>原因

可能未受信任的 HTTP 要求輸入到達檔案作業的路徑。

## <a name="rule-description"></a>規則描述

當您使用來自 web 要求的未受信任輸入時，請留意在指定檔案路徑時使用使用者控制的輸入。 攻擊者可能會讀取非預期的檔案，而導致敏感性資料的資訊洩漏。 或者，攻擊者可能可以寫入非預期的檔案，因而導致未經授權的敏感性資料修改或危害伺服器的安全性。 常見的攻擊者技術是[路徑遍歷](https://www.owasp.org/index.php/Path_Traversal)，可存取預定目錄以外的檔案。

此規則會嘗試在檔案作業中尋找到達路徑的 HTTP 要求輸入。

> [!NOTE]
> 此規則無法跨元件追蹤資料。 例如，如果一個元件讀取 HTTP 要求輸入，然後將它傳遞給另一個寫入檔案的元件，此規則就不會產生警告。

> [!NOTE]
> 此規則會在方法呼叫中分析資料流的深度有一個可設定的限制。 如需如何在 EditorConfig 檔中設定限制的詳細說明，請參閱[分析器](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis)設定。

## <a name="how-to-fix-violations"></a>如何修正違規

- 可能的話，請根據使用者輸入，將檔案路徑限制為明確已知的安全清單。  例如，如果您的應用程式只需要存取 "red .txt"、"綠 .txt" 或 "blue .txt"，則只會允許這些值。
- 檢查是否有不受信任的檔案名，並驗證名稱的格式是否正確。
- 指定路徑時，請使用完整路徑名稱。
- 避免潛在危險的結構，例如 path 環境變數。
- 如果使用者提交簡短名稱，則只接受長檔名，並驗證完整名稱。
- 將使用者輸入限制為有效的字元。
- 拒絕超過 MAX_PATH 長度的名稱。
- 逐文書處理檔案名，不進行轉譯。
- 判斷檔案名是否代表檔案或裝置。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您已依照上一節所述的方式驗證輸入，就可以隱藏這個警告。

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
