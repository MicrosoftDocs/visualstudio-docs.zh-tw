---
title: 如何：使用 __analysis_assume 指定額外的程式碼資訊 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: f2f18c9284ec96de7a7b8663aff485962d194282
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277969"
---
# <a name="how-to-specify-additional-code-information-by-using-__analysis_assume"></a>如何：使用 __analysis_assume 指定其他程式碼資訊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以為 C/C++ code 提供程式碼分析工具的提示，以協助分析程式並減少警告。 若要提供其他資訊，請使用下列函數：  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr`-假設評估為 true 的任何運算式。  
  
 程式碼分析工具假設運算式所表示的條件在函式出現的時間點為 true，而且在改變運算式之前會保持為 true，例如，藉由將指派給變數。  
  
> [!NOTE]
> `__analysis_assume` 不會影響程式碼優化。 在程式碼分析工具之外，`__analysis_assume` 會定義為無 op。  
  
## <a name="example"></a>範例  
 下列程式碼會使用 `__analysis_assume` 來更正程式碼分析警告[C6388](../code-quality/c6388.md)：  
  
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
  __analysis_assume(pc == NULL);   
  f(pc);  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [__assume](https://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
