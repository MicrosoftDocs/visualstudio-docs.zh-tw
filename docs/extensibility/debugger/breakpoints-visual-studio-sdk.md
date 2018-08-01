---
title: 中斷點 (Visual Studio SDK) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1aa5fe2ffba7660b3a5774a865572bf10446f09a
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152639"
---
# <a name="breakpoints-visual-studio-sdk"></a>中斷點 (Visual Studio SDK)
有三種中斷點類型： 暫止、 繫結和錯誤。  
  
 **暫止的中斷點：**  
  
-   是包含將中斷點繫結至一個或多個程式中的一或多個程式碼內容所需的所有資訊的抽象概念。 每次程式正在偵錯原因可載入的程式碼的偵錯引擎會檢查以查看 是否可以結合的所有暫止中斷點。  
  
     暫止中斷點本身永遠不會繫結至程式碼，但而是會收集，所以包含它所產生的所有繫結的中斷點。  
  
-   由[IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面。  
  
 **繫結的中斷點：**  
  
-   是中斷點的抽象概念與相關聯，或繫結到單一程式碼內容。 每個繫結的中斷點會產生回應的暫止中斷點。 暫止中斷點可以不過，產生一個以上的繫結的中斷點。  
  
     卸載程式碼時，就可以解除繫結並捨棄繫結的中斷點。  
  
-   由[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)介面。  
  
 **錯誤中斷點：**  
  
-   為描述錯誤中嘗試暫止中斷點繫結程式碼內容的抽象概念。 其中一個錯誤在位置或中斷點運算式本身說明錯誤中斷點。 如需詳細資訊，請參閱 <<c0> [ 繫結中斷點](../../extensibility/debugger/binding-breakpoints.md)。  
  
     中斷點錯誤可以是錯誤或警告。  
  
-   由[IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [程式](../../extensibility/debugger/programs.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [程式碼內容](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)