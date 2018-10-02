---
title: 如何： 使用 __analysis_assume 指定其他程式碼資訊 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a08ca5a35d08f284062323f2e75648852debb7bf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490143"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>如何：使用 __analysis_assume 指定其他程式碼資訊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 使用 __analysis_assume 指定其他的程式碼資訊](https://docs.microsoft.com/visualstudio/code-quality/how-to-specify-additional-code-information-by-using-analysis-assume)。  
  
您可以提供程式碼分析工具的提示會協助分析程序，並減少警告的 C/c + + 程式碼。 若要提供其他資訊，請使用下列函式：  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` -假設為評估為 true 的任何運算式。  
  
 程式碼分析工具假設條件運算式所代表之處函式隨即出現，並保持為 true，直到運算式改變，例如，藉由指派給變數，則為 true。  
  
> [!NOTE]
>  `__analysis_assume` 不會影響程式碼最佳化。 外部程式碼分析工具，`__analysis_assume`定義為執行任何作業。  
  
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



