---
title: 文字範本公用程式方法
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e6426ea57fbdbec6ec47a4f6348463b88b250e0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606014"
---
# <a name="text-template-utility-methods"></a>文字範本公用程式方法

當您在 Visual Studio 文字模板中撰寫程式碼時，一定會有數種方法可供您使用。 這些方法會在 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> 中定義。

> [!TIP]
> 您也可以在一般（未預先處理的）文字模板中，使用主機環境所提供的其他方法和服務。 例如，您可以解析檔案路徑、記錄錯誤，並取得 Visual Studio 和任何載入的封裝所提供的服務。 如需詳細資訊，請參閱[從文字模板存取 Visual Studio](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\))。

## <a name="write-methods"></a>Write 方法

您可以使用 `Write()` 和 `WriteLine()` 方法，將文字附加至標準程式碼區塊內，而不是使用運算式程式碼區塊。 下列兩個程式碼區塊的功能相同。

### <a name="code-block-with-an-expression-block"></a>具有運算式區塊的程式碼區塊

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>使用 WriteLine （）的程式碼區塊

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

在具有嵌套控制項結構的長程式碼區塊內使用其中一種公用程式方法，而不是運算式區塊，可能會很有説明。

@No__t_0 和 `WriteLine()` 方法有兩個多載，一個會採用單一字串參數，另一個則採用複合格式字串，再加上要包含在字串中的物件陣列（例如 `Console.WriteLine()` 方法）。 @No__t_0 的下列兩個用法在功能上是相同的：

```
<#
    string msg = "Say: {0}, {1}, {2}";
    string s1 = "hello";
    string s2 = "goodbye";
    string s3 = "farewell";

    WriteLine(msg, s1, s2, s3);
    WriteLine("Say: hello, goodbye, farewell");
#>
```

## <a name="indentation-methods"></a>縮排方法

您可以使用縮排方法來格式化文字模板的輸出。 @No__t_0 類別具有 `CurrentIndent` 字串屬性，它會顯示文字模板中目前的縮排，以及已加入的縮圖清單 `indentLengths` 欄位。 您可以使用 `PushIndent()` 方法加入縮排，並使用 `PopIndent()` 方法來減去縮排。 如果您想要移除所有縮排，請使用 `ClearIndent()` 方法。 下列程式碼區塊顯示這些方法的用法：

```
<#
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    ClearIndent();
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
#>
```

此程式碼區塊會產生下列輸出：

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>錯誤和警告方法

您可以使用錯誤和警告公用程式方法，將訊息新增至 Visual Studio 錯誤清單。 例如，下列程式碼會將錯誤訊息新增至錯誤清單。

```
<#
  try
  {
    string str = null;
    Write(str.Length.ToString());
  }
  catch (Exception e)
  {
    Error(e.Message);
  }
#>
```

## <a name="access-to-host-and-service-provider"></a>存取主機和服務提供者

屬性 `this.Host` 可以提供執行範本之主機所公開之屬性的存取權。 若要使用 `this.Host`，您必須在 `<@template#>` 指示詞中設定 `hostspecific` 屬性：

`<#@template ... hostspecific="true" #>`

@No__t_0 的類型取決於範本執行所在的主機類型。 在 Visual Studio 中執行的範本中，您可以將 `this.Host` 轉換成 `IServiceProvider`，以取得 IDE 等服務的存取權。 例如:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>使用一組不同的公用程式方法

做為文字產生程式的一部分，您的範本檔案會轉換為類別，而此類別一律會命名為 `GeneratedTextTransformation`and 繼承自 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。 如果您想要改為使用一組不同的方法，您可以撰寫自己的類別，並在範本指示詞中指定它。 您的類別必須繼承自 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。

```
<#@ template inherits="MyUtilityClass" #>
```

使用 `assembly` 指示詞來參考可以找到編譯類別的元件。