---
title: 叫用中斷點 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5ae077b8ccb4ce41f94fbc5e11bfff1f16c826c0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941505"
---
# <a name="hitting-a-breakpoint"></a>到達中斷點
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

以下說明當偵錯引擎 (DE) 叫用中斷點時執行，或逐步執行的程序：  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>疑難排解點擊的中斷點  
  
1.  DE 傳送[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)介面做**EVENT_SYNC_STOP**。  
  
2.  工作階段的偵錯管理員 (SDM) 會呼叫[IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)取得已點擊的中斷點。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
