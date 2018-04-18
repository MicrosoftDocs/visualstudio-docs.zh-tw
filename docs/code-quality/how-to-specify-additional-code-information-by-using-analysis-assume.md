---
title: 如何： 使用 __analysis_assume 指定其他程式碼資訊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f039298e56e33bc80ae1a9f7384a40914c532ff8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>如何：使用 __analysis_assume 指定其他程式碼資訊
C/c + + 程式碼，將會協助分析程序，並減少警告，您可以提供程式碼分析工具提示。 若要提供其他資訊，請使用下列函數：  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` -假設為評估為 true 的任何運算式。  
  
 程式碼分析工具假設條件運算式所表示的點函式隨即出現，並保持為 true，直到運算式改變，例如，藉由指派給變數，則為 true。  
  
> [!NOTE]
>  `__analysis_assume` 不會影響程式碼最佳化。 外部程式碼分析工具，`__analysis_assume`定義為任何作業。  
  
## <a name="example"></a>範例  
 下列程式碼會使用`__analysis_assume`更正程式碼分析警告[C6388](../code-quality/c6388.md):  
  
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
 [__assume](/cpp/intrinsics/assume)