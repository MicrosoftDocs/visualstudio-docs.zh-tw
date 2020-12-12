---
title: T4 輸出指示詞
description: 瞭解 Visual Studio 文字模板中，output 指示詞是用來定義已轉換之檔案的副檔名和編碼。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9849a326549aa534d9cd558337b825b7e0b8d1f
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363636"
---
# <a name="t4-output-directive"></a>T4 輸出指示詞

在 Visual Studio 文字模板中，指示詞 `output` 是用來定義已轉換之檔案的副檔名和編碼。

 例如，如果您的 Visual Studio 專案包含名為 **MyTemplate.tt** 的範本檔案，其中包含下列指示詞：

 `<#@output extension=".cs"#>`

 然後 Visual Studio 會產生名為 **MyTemplate.cs** 的檔案。

 在執行階段 (前置處理過的) 文字範本中，不需要 `output` 指示詞。 而是，您的應用程式會呼叫 `TextTransform()` 來取得產生的字串。 如需詳細資訊，請參閱 [使用 T4 文字模板的執行時間文字產生](../modeling/run-time-text-generation-with-t4-text-templates.md)。

## <a name="using-the-output-directive"></a>使用輸出指示詞

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 在每個文字範本中，不應該有多個 `output` 指示詞。

## <a name="extension-attribute"></a>extension 屬性
 指定所產生文字輸出檔案的副檔名。

 預設值為 **.cs。**

 範例：`<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 可接受的值：任何有效的副檔名。

## <a name="encoding-attribute"></a>encoding 屬性
 指定要在產生輸出檔案時使用的編碼。 例如：

 `<#@ output encoding="utf-8"#>`

 預設值是文字範本檔所使用的編碼。

 可接受的值： `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (系統預設) 

 一般而言，您可以使用 <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> 所傳回之任何編碼的 WebName 字串或 CodePage 號碼。
