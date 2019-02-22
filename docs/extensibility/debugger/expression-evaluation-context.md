---
title: 運算式評估內容 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 25dc88025a6fb4c4efe83d0c77c288e126cec1b2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957283"
---
# <a name="expression-evaluation-context"></a>運算式評估內容
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯**運算式評估內容**:  
  
-   表示運算式評估的內容。 通常，評估內容會對應至在其中評估變數、 參數、 函數和方法的語彙範圍。 比方說，堆疊框架相關聯的運算式評估內容將提供的內容，來評估區域變數、 方法參數和類別成員 （如果適用）。  
  
-   當程式已經在中斷點停止時，就會存在。 運算式本身是資料結構，表示剖析的運算式，供繫結和指定的內容內評估。  
  
     在詳細資料，運算式會建立使用[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法。 評估運算式時，它會產生可列印的字串，包含名稱和類型的變數或引數，而其值。 在 [監看式] 視窗或 IDE 的 [區域變數] 視窗中，會顯示這個字串。  
  
     給定`BSTR`並[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面，可以建立偵錯引擎 (DE) [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面藉由剖析運算式。 指定`IDebugExpression2`介面，DE 可以取得透過同步或非同步運算式評估的值。 此值的名稱和類型的變數或引數，以及顯示會傳送到 IDE。  
  
## <a name="see-also"></a>另請參閱  
 [運算式評估介面](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)