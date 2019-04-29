---
title: 文字範本公用程式方法
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c65960b2ad7f0eb31a9c969fb4671f883dc477c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001473"
---
# <a name="text-template-utility-methods"></a>文字範本公用程式方法

有數種方法，都可供您，當您在 Visual Studio 文字範本中撰寫程式碼。 這些方法的定義位於<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。

> [!TIP]
> 您也可以使用其他方法和一般 （不前置處理過的） 文字範本中的主機環境所提供的服務。 比方說，您可以在此解析檔案路徑、 記錄錯誤，並取得 Visual Studio 及任何所提供的服務已載入的套件。 如需詳細資訊，請參閱 <<c0> [ 從文字範本存取 Visual Studio](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\))。

## <a name="write-methods"></a>撰寫方法

您可以使用`Write()`和`WriteLine()`方法來附加在標準的程式碼區塊，而不是使用運算式的程式碼區塊內的文字。 下列兩個程式碼區塊的功能相同。

### <a name="code-block-with-an-expression-block"></a>運算式區塊的程式碼區塊

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>使用 writeline （） 的程式碼區塊

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

您可能會發現若要使用其中一個這些公用程式方法，而不是運算式區塊程式碼區塊中使用巢狀的控制結構很有幫助。

`Write()`並`WriteLine()`方法有兩個多載，另一個會採用單一字串參數，一個會複合格式字串以及要包含在字串中的物件陣列 (例如`Console.WriteLine()`方法)。 下列兩種用法`WriteLine()`相同的功能：

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

您可以使用縮排方法來格式化文字範本的輸出。 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>類別具有`CurrentIndent`字串會顯示目前的縮排文字範本中的屬性和`indentLengths`欄位也就是已加入縮排的清單。 您可以加入與縮排`PushIndent()`方法並減去使用縮排`PopIndent()`方法。 如果您想要移除所有的縮排，使用`ClearIndent()`方法。 下列程式碼區塊顯示使用這些方法：

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

您可以使用錯誤和警告公用程式方法，將訊息新增至 Visual Studio 錯誤清單。 比方說，下列程式碼會將錯誤訊息新增至 錯誤清單。

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

## <a name="access-to-host-and-service-provider"></a>存取主應用程式和服務提供者

屬性`this.Host`可存取主機正在執行範本所公開的屬性。 若要使用`this.Host`，您必須設定`hostspecific`屬性中`<@template#>`指示詞：

`<#@template ... hostspecific="true" #>`

型別`this.Host`範本執行所在的主控件的類型而定。 在範本中執行 Visual Studio 中，您可以轉型`this.Host`至`IServiceProvider`來存取服務，例如 IDE。 例如: 

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>使用一組不同的公用程式方法

文字產生程序的一部分，您的範本檔案會轉換成的類別名稱永遠是`GeneratedTextTransformation`是繼承自<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。 如果您想要使用不同的一組方法相反地，您可以撰寫您自己的類別並在範本指示詞中指定它。 您的類別必須繼承自<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。

```
<#@ template inherits="MyUtilityClass" #>
```

使用`assembly`指示詞來參考組件可在其中找到編譯的類別。