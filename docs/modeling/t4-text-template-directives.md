---
title: T4 文字範本指示詞
description: 瞭解 T4 測試範本指示詞，以及它們如何提供文字模板轉換引擎的指示。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ddad0010413ebe8e0a53096bb4d90b52050d26a
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363597"
---
# <a name="t4-text-template-directives"></a>T4 文字範本指示詞

指示詞會提供指令給文字範本轉換引擎。

指示詞的語法如下：

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

所有屬性值都必須包含在雙引號中。 如果值本身包含引號，則必須以 \ 字元逸出。

指示詞通常是範本檔案或被納入的檔案中的第一個項目。 在 `<#...#>` 程式碼區塊內，或 `<#+...#>` 類別功能區塊後面，都不應該放置指示詞。

[T4 範本指示詞](../modeling/t4-template-directive.md)

```
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>
```

[T4 參數指示詞](../modeling/t4-parameter-directive.md)

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

[T4 輸出指示詞](../modeling/t4-output-directive.md)

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

[T4 組件指示詞](../modeling/t4-assembly-directive.md)

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

[T4 匯入指示詞](../modeling/t4-import-directive.md)

```
<#@ import namespace="namespace" #>
```

[T4 包含指示詞](../modeling/t4-include-directive.md)

```
<#@ include file="filePath" #>
```

[T4 CleanUpBehavior 指示詞](../modeling/t4-cleanupbehavior-directive.md)

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

此外，您也可以建立自己的指示詞。 如需詳細資訊，請參閱 [建立自訂 T4 文字模板](../modeling/creating-custom-t4-text-template-directive-processors.md)指示詞處理器。 如果使用 Visualization and Modeling SDK 建立特定領域語言 (DSL)，則會產生指示詞處理器做為 DSL 的一部分。
