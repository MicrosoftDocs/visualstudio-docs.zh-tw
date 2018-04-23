---
title: 叫用中斷點 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f4788f8a038a274d6d94b4edf368e30ef495665
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="hitting-a-breakpoint"></a>叫用中斷點
以下描述的偵錯引擎 (DE) 執行，或逐步執行時叫用中斷點時的處理程序：  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>疑難排解點擊的中斷點  
  
1.  DE 傳送[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)介面做**EVENT_SYNC_STOP**。  
  
2.  工作階段的偵錯管理員 (SDM) 呼叫[IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)取得已點擊的中斷點。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)