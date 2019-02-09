---
title: T4 輸出指示詞
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfbe77f5b6e2bbda6a51d392c4dd16b079100e81
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952381"
---
# <a name="t4-output-directive"></a>T4 輸出指示詞

在 Visual Studio 文字範本中，`output`指示詞用來定義檔案的副檔名和編碼轉換檔案。

 例如，如果您的 Visual Studio 專案包含名為範本檔**MyTemplate.tt**其中包含下列指示詞：

 `<#@output extension=".cs"#>`

 Visual Studio 會產生名為的檔案，然後**MyTemplate.cs**

 在執行階段 (前置處理過的) 文字範本中，不需要 `output` 指示詞。 而是，您的應用程式會呼叫 `TextTransform()` 來取得產生的字串。 如需詳細資訊，請參閱 <<c0> [ 執行階段使用 T4 文字範本產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。

## <a name="using-the-output-directive"></a>使用輸出指示詞

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 在每個文字範本中，不應該有多個 `output` 指示詞。

## <a name="extension-attribute"></a>擴充屬性
 指定所產生文字輸出檔案的副檔名。

 預設值是 **.cs**

 範例： `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 可接受值：任何有效的副檔名。

## <a name="encoding-attribute"></a>編碼方式屬性
 指定要在產生輸出檔案時使用的編碼。 例如：

 `<#@ output encoding="utf-8"#>`

 預設值是文字範本檔所使用的編碼。

 可接受的值： `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (系統預設值)

 一般而言，您可以使用 <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> 所傳回之任何編碼的 WebName 字串或 CodePage 號碼。