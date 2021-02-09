---
title: 文字範本公用程式方法
description: 瞭解當您在 Visual Studio 中撰寫程式碼時，可供您使用的各種文字模板公用程式方法。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fcc879a19d3dfcd9e1e8e1bcd79f0488a312e96c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924565"
---
# <a name="text-template-utility-methods"></a>文字範本公用程式方法

當您在 Visual Studio 文字模板中撰寫程式碼時，有數種方法一律可供您使用。 這些方法是在中定義 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> 。

> [!TIP]
> 您也可以在一般 (未預先處理的) 文字模板中，使用主機環境所提供的其他方法和服務。 例如，您可以解析檔案路徑、記錄錯誤，以及取得 Visual Studio 和任何載入的封裝所提供的服務。 如需詳細資訊，請參閱 [從文字模板存取 Visual Studio](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\))。

## <a name="write-methods"></a>Write 方法

您可以使用 `Write()` 和 `WriteLine()` 方法，在標準程式碼區塊內附加文字，而不是使用運算式程式碼區塊。 下列兩個程式碼區塊的功能相同。

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

### <a name="code-block-using-writeline"></a>使用 WriteLine ( # A1 的程式碼區塊

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

您可能會發現，在具有嵌套控制項結構的長程式碼區塊內使用其中一種公用程式方法，而不是運算式區塊，會很有説明。

`Write()`和 `WriteLine()` 方法有兩個多載，其中一個會採用單一字串參數，另一個則採用複合格式字串，加上一個採用複合格式字串的物件陣列，以及要包含在字串中的物件陣列 (例如 `Console.WriteLine()`) 方法。 下列兩個用途在 `WriteLine()` 功能上相同：

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

您可以使用縮排方法來格式化文字模板的輸出。 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>類別具有 `CurrentIndent` 字串屬性，可顯示文字模板中目前的縮排，以及已 `indentLengths` 加入之縮排清單的欄位。 您可以使用方法來新增縮排 `PushIndent()` ，並使用方法來減去縮排 `PopIndent()` 。 如果您想要移除所有縮排，請使用 `ClearIndent()` 方法。 下列程式碼區塊顯示如何使用這些方法：

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

這個程式碼區塊會產生下列輸出：

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>錯誤和警告方法

您可以使用錯誤和警告公用程式方法，將訊息新增至 Visual Studio 錯誤清單。 例如，下列程式碼會將錯誤訊息加入至錯誤清單。

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

## <a name="access-to-host-and-service-provider"></a>主機和服務提供者的存取權

屬性 `this.Host` 可讓您存取執行範本的主機所公開的屬性。 若要使用 `this.Host` ，您必須 `hostspecific` 在指示詞中設定屬性 `<@template#>` ：

`<#@template ... hostspecific="true" #>`

的類型 `this.Host` 取決於範本執行所在的主控制項類型。 在 Visual Studio 中執行的範本中，您可以將轉換 `this.Host` 為， `IServiceProvider` 以取得 IDE 等服務的存取權。 例如：

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>使用一組不同的公用程式方法

在文字產生程式中，會將您的範本檔案轉換成永遠會命名 `GeneratedTextTransformation` 和繼承自的類別 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> 。 如果您想要改用一組不同的方法，您可以撰寫自己的類別，並在範本指示詞中指定它。 您的類別必須繼承自 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> 。

```
<#@ template inherits="MyUtilityClass" #>
```

使用指示詞 `assembly` 來參考可找到編譯類別的元件。
