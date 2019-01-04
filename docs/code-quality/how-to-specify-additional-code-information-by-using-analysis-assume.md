---
title: HOW TO：使用 _Analysis_assume 來指定其他程式碼資訊
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 17e25ace1da6cad9fcdc129b6c6f517c39c9c103
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845074"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>HOW TO：使用 _Analysis_assume 來指定其他程式碼資訊
您可以提供程式碼分析工具的提示會協助分析程序，並減少警告的 C/c + + 程式碼。 若要提供其他資訊，請使用下列函式：

 `_Analysis_assume(`  `expr`  `)`

 `expr` -假設為評估為 true 的任何運算式。

 程式碼分析工具假設條件運算式所代表之處函式隨即出現，並保持為 true，直到運算式改變，例如，藉由指派給變數，則為 true。

> [!NOTE]
>  `_Analysis_assume` 不會影響程式碼最佳化。 外部程式碼分析工具，`_Analysis_assume`定義為執行任何作業。

## <a name="example"></a>範例
 下列程式碼會使用`_Analysis_assume`若要修正程式碼分析警告[C6388](../code-quality/c6388.md):

```
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

// calls free and sets ch to null
void FreeAndNull(char* ch);

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

void test( )
{
  char *pc = (char*)malloc(5);
  FreeAndNull(pc);
  _Analysis_assume(pc == NULL);
  f(pc);
}
```

## <a name="see-also"></a>另請參閱
 [__assume](/cpp/intrinsics/assume)