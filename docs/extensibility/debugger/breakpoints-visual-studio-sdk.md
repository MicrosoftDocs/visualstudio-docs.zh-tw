---
title: 中斷點 (Visual Studio SDK) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: be8f0b36ebe57041e9d36b8f606bd5bddd0601bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="breakpoints-visual-studio-sdk"></a>中斷點 (Visual Studio SDK)
有三種中斷點類型： 暫止，繫結，以及錯誤。  
  
 **暫止中斷點：**  
  
-   是抽象，其中包含中斷點繫結至一個或多個程式中的一或多個程式碼內容所需的所有資訊。 每次的程式進行偵錯原因来載入的程式碼，偵錯引擎會檢查以查看是否它們可以繫結的所有暫止中斷點。  
  
     暫止中斷點本身永遠不會將繫結至程式碼中，而是會收集和稱為以包含所有繫結的中斷點，它會產生。  
  
-   由[IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面。  
  
 **繫結的中斷點：**  
  
-   中斷點的抽象概念是與相關聯或繫結到單一程式碼內容。 每個繫結的中斷點暫止中斷點的回應中產生。 暫止中斷點可以不過，產生一個以上的繫結的中斷點。  
  
     程式碼卸載時，可以未繫結的繫結的中斷點，並捨棄。  
  
-   由[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)介面。  
  
 **錯誤中斷點：**  
  
-   是在嘗試將暫止中斷點繫結至程式碼內容描述錯誤的抽象概念。 其中一個錯誤或中斷點運算式本身的位置中說明錯誤中斷點。 如需詳細資訊，請參閱[繫結中斷點](../../extensibility/debugger/binding-breakpoints.md)。  
  
     中斷點錯誤可以是錯誤或警告。  
  
-   由[IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)介面。  
  
## <a name="see-also"></a>請參閱  
 [程式](../../extensibility/debugger/programs.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [程式碼內容](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)