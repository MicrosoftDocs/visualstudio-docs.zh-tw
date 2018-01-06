---
title: "運算式評估內容 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ab4e57f500c2dfbfe673713c784cbc93ff52a73d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="expression-evaluation-context"></a>運算式評估內容
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯，**運算式評估內容**:  
  
-   表示運算式評估的內容。 通常，評估內容會對應至在其中評估變數、 參數、 函數和方法的語彙範圍。 例如，運算式評估內容相關聯的堆疊框架將會提供內容評估本機變數、 方法參數和類別成員 （如果適用）。  
  
-   當程式已經在中斷點停止時，就會存在。 運算式本身是代表已繫結和指定的內容中評估的已剖析的運算式的資料結構。  
  
     在詳細資料，運算式會建立使用[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法。 評估運算式時，它會產生可列印的字串，包含名稱和類型變數或引數和其值。 這個字串會顯示在 [監看式] 視窗或在 IDE 的 [區域變數] 視窗中。  
  
     指定`BSTR`和[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面，可以建立偵錯引擎 (DE) [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)藉由剖析運算式的介面。 指定`IDebugExpression2`介面，DE 可以取得透過同步或非同步的運算式評估的值。 顯示此值的名稱和類型的變數或引數，以及傳送給 IDE。  
  
## <a name="see-also"></a>請參閱  
 [運算式評估介面](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)