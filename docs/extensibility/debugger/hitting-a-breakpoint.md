---
title: "叫用中斷點 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dfdf86124bdaf9160121b7d93263dc1d60425515
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="hitting-a-breakpoint"></a>叫用中斷點
以下描述的偵錯引擎 (DE) 執行，或逐步執行時叫用中斷點時的處理程序：  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>疑難排解點擊的中斷點  
  
1.  DE 傳送[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)介面做**EVENT_SYNC_STOP**。  
  
2.  工作階段的偵錯管理員 (SDM) 呼叫[IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)取得已點擊的中斷點。  
  
## <a name="see-also"></a>請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)