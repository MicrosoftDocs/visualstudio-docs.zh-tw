---
title: HOW TO：使用 __analysis_assume 指定其他程式碼資訊 |Microsoft Docs
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
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: e130f2248ae6715b3248226c780bc162e1ff01ef
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426633"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>HOW TO：使用 _analysis_assume 來指定其他程式碼資訊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以提供提示給程式碼分析工具，適用於 C /C++可協助分析處理，並減少警告的程式碼。 若要提供其他資訊，請使用下列函式：  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` -假設為評估為 true 的任何運算式。  
  
 程式碼分析工具假設條件運算式所代表之處函式隨即出現，並保持為 true，直到運算式改變，例如，藉由指派給變數，則為 true。  
  
> [!NOTE]
> `__analysis_assume` 不會影響程式碼最佳化。 外部程式碼分析工具，`__analysis_assume`定義為執行任何作業。  
  
## <a name="example"></a>範例  
 下列程式碼會使用`__analysis_assume`若要修正程式碼分析警告[C6388](../code-quality/c6388.md):  
  
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
 [__assume](http://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
