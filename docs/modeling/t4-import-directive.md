---
title: T4 匯入指示詞
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74181ea3bb086688893749850adb697c75b6eac1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606447"
---
# <a name="t4-import-directive"></a>T4 匯入指示詞

在 Visual Studio T4 文字模板的程式碼區塊中，`import` 指示詞可讓您參考另一個命名空間中的元素，而不需要提供完整名稱。 這個指示詞相當於 C# 中的 `using` 或 `imports` 中的 [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)]。

如需撰寫 T4 文字模板的一般總覽，請參閱[撰寫 T4 文字模板](../modeling/writing-a-t4-text-template.md)。

## <a name="using-the-import-directive"></a>使用匯入指示詞

```
<#@ import namespace="namespace" #>
```

 在這個範例中，範本程式碼會省略 System.IO 成員的明確命名空間。

```
<#@ import namespace="System.IO" #>
<#
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File
#>
The file contains: <#=  fileContent #>
```

## <a name="standard-imports"></a>標準匯入
 下列命名空間會自動匯入，因此您不需要為它撰寫 import 指示詞：

- `System`

  此外，如果使用自訂指示詞，指示詞處理器可能會自動匯入一些組件。

  例如，如果撰寫網域指定的語言 (DSL)，就不需要為下列命名空間撰寫 import 指示詞：

- `Microsoft.VisualStudio.Modeling`

- DSL 的命名空間

## <a name="see-also"></a>請參閱

- [T4 組件指示詞](../modeling/t4-assembly-directive.md)