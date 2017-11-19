---
title: "中斷點錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9c197bbaf8fb79ea4396c7b2e36af94d59c7ea8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="breakpoint-errors"></a>中斷點錯誤
下列中斷點嘗試繫結至程式碼時，描述的程序，但是會失敗：  
  
## <a name="troubleshooting-a-breakpoint-error"></a>中斷點錯誤疑難排解  
  
1.  偵錯引擎 (DE) 傳送[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)到工作階段的偵錯管理員 (SDM)。  
  
2.  SDM 呼叫[IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP`) 以取得錯誤中斷點。  
  
3.  SDM 呼叫[IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)取得來源錯誤中斷點暫止中斷點。  
  
4.  SDM 呼叫[IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)以取得錯誤中斷點繫結失敗的原因。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)