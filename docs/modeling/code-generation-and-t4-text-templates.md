---
title: 程式碼產生和 T4 文字範本
description: 瞭解 T4 文字模板如何混用可產生文字檔的文字區塊和控制邏輯。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 871aa20fe4fc95ea1641b7f478cb9b01d71284aa
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363571"
---
# <a name="code-generation-and-t4-text-templates"></a>程式碼產生和 T4 文字範本

在 Visual Studio 中， *T4 文字模板* 是混合的文字區塊和控制邏輯，可產生文字檔。 控制邏輯是由 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 或 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]撰寫的程式碼片段。 在 Visual Studio 2015 Update 2 (含) 以後版本中，您可以在 T4 範本指示詞中使用 C# 6.0 版功能。 產生的檔案可以是任何類型的文字，例如網頁、資源檔或任何語言的程式原始程式碼。

T4 文字模板有兩種：執行時間和設計階段。

## <a name="run-time-t4-text-templates"></a>執行時間 T4 文字模板

也稱為「前置處理過的」範本，執行時間範本會在您的應用程式中執行，以產生文字字串，通常是其輸出的一部分。 例如，您可以建立用來定義 HTML 網頁的範本：

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

請注意，範本與產生的輸出類似。 範本與產生的輸出之間的相似性，可協助您避免在要變更範本時發生錯誤。

此外，範本也包含程式碼片段。 您可以使用這些片段來重複文字區段、建立條件式區段，以及顯示應用程式的資料。

為產生輸出，應用程式會呼叫範本所產生的函式。 例如：

```csharp
string webResponseText = new MyTemplate().TransformText();
```

您的應用程式可以在未安裝 Visual Studio 的電腦上執行。

若要建立執行階段範本，請將 [前置處理過的文字範本]  檔案加入專案中。 此外，您也可以加入純文字檔，並將其 [自訂工具]  屬性設定為 [TextTemplatingFilePreprocessor] 。

如需詳細資訊，請參閱 [使用 T4 文字模板的執行時間文字產生](../modeling/run-time-text-generation-with-t4-text-templates.md)。 如需範本語法的詳細資訊，請參閱 [撰寫 T4 文字模板](../modeling/writing-a-t4-text-template.md)。

## <a name="design-time-t4-text-templates"></a>設計階段 T4 文字模板

設計階段範本會定義原始程式碼的一部分，以及應用程式的其他資源。 通常您會使用數個範本，以讀取單一輸入檔案或資料庫中的資料，並產生一些 *.cs*、 *.vb* 或其他原始程式檔。 每個範本都會產生一個檔案， 它們會在 Visual Studio 或 MSBuild 內執行。

例如，輸入資料可以是組態資料的 XML 檔案。 當您在開發期間編輯 XML 檔案時，文字模板會重新產生部分的應用程式程式碼。 其中一個範本可能類似下列範例：

```
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}
```

根據 XML 檔案中的值，產生的 *.cs* 檔案如下所示：

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

另一個範例是，輸入可以是商務活動中的工作流程圖。 當使用者變更其商務工作流程，或您與工作流程不同的新使用者開始合作時，就可以輕鬆地重新產生符合新模型的程式碼。

設計階段範本可讓您在需求變更時，更快速且可靠地變更組態。 如工作流程範例所示，輸入通常是依照商務需求定義的。 這可讓您更容易與使用者討論變更。 因此，設計階段範本對敏捷式開發流程來說是很有用的工具。

若要建立設計階段範本，請將 [文字範本]  檔案加入專案中。 此外，您也可以加入純文字檔，並將其 [自訂工具]  屬性設定為 [TextTemplatingFileGenerator] 。

如需詳細資訊，請參閱 [使用 T4 文字模板的設計階段程式碼產生](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。 如需範本語法的詳細資訊，請參閱 [撰寫 T4 文字模板](../modeling/writing-a-t4-text-template.md)。

> [!NOTE]
> *「模型」* (model) 一詞有時可用來描述由一個或多個範本讀取的資料。 模型可以是任何形式、任何類型的檔案或資料庫。 它不需要是 UML 模型或「特定領域語言」模型。 「模型」只表示資料可以依照商務概念定義，而非類似於程式碼。

文字範本轉換功能的名稱為 *T4*。

## <a name="see-also"></a>請參閱

- [從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)
