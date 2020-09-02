---
title: 觸達中斷點 |Microsoft Docs
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
ms.openlocfilehash: 0ddf7fd92ac0b2f745f9e73170de22e9724dad76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152691"
---
# <a name="hitting-a-breakpoint"></a>到達中斷點
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

以下描述當 debug engine (DE) 在執行或逐步執行時叫用中斷點時的程式：  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>針對點擊中斷點進行疑難排解  
  
1. 「取消」會將 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 介面傳送成 **EVENT_SYNC_STOP**。  
  
2. 會話 debug manager (SDM) 呼叫 [IDebugBreakpointEvent2：：： EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) 來取得點擊的中斷點。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
