---
title: T4 匯入指示詞
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6b0479bf427930d19b12fa0de5728f26e7cdb10d
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510174"
---
# <a name="t4-import-directive"></a>T4 匯入指示詞

中的程式碼區塊[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]T4 文字範本，`import`指示詞可讓您參考另一個命名空間中的項目，而不需提供完整的名稱。 這個指示詞相當於 C# 中的 `using` 或 `imports` 中的 [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)]。

撰寫 T4 文字範本的一般概觀，請參閱 <<c0> [ 撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)。

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

-   `System`

 此外，如果使用自訂指示詞，指示詞處理器可能會自動匯入一些組件。

 例如，如果撰寫特定領域語言 (DSL)，就不需要為下列命名空間撰寫 import 指示詞：

-   `Microsoft.VisualStudio.Modeling`

-   DSL 的命名空間

## <a name="see-also"></a>另請參閱

- [T4 組件指示詞](../modeling/t4-assembly-directive.md)