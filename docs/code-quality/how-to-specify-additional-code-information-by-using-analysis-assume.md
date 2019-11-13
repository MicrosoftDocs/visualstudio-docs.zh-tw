---
title: 使用 _Analysis_assume 的程式碼分析提示
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 9933a013ed4f2df0978fb66e3aff87b4cdc024f9
ms.sourcegitcommit: c6af923c1f485959d751b23ab3f03541013fc4a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73925954"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>如何：使用 _Analysis_assume 指定額外的程式碼資訊

您可以為 C/C++ code 提供程式碼分析工具的提示，以協助分析程式並減少警告。 若要提供其他資訊，請使用下列函數：

`_Analysis_assume(`  `expr`  `)`

`expr`-假設評估為 true 的任何運算式。

程式碼分析工具假設運算式所表示的條件在函式出現的時間點為 true，而且在改變運算式之前會保持為 true，例如，藉由將指派給變數。

> [!NOTE]
> `_Analysis_assume` 不會影響程式碼優化。 在程式碼分析工具之外，`_Analysis_assume` 會定義為無 op。

## <a name="example"></a>範例

下列程式碼會使用 `_Analysis_assume` 來更正程式碼分析警告[C6388](../code-quality/c6388.md)：

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    _Analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>請參閱

- [__assume](/cpp/intrinsics/assume)
