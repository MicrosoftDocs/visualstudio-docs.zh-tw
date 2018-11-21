---
title: 中斷點錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7614a82e4c25c2896fa98ba9685de0a6a5920fbc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770807"
---
# <a name="breakpoint-errors"></a>中斷點錯誤
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

以下說明的程序時嘗試繫結至程式碼的中斷點，但失敗：  
  
## <a name="troubleshooting-a-breakpoint-error"></a>中斷點錯誤疑難排解  
  
1.  偵錯引擎 (DE) 會傳送[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)工作階段的偵錯管理員 (SDM)。  
  
2.  SDM 呼叫[IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP`) 以取得錯誤的中斷點。  
  
3.  SDM 呼叫[IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)取得從中產生錯誤的中斷點暫止中斷點。  
  
4.  SDM 呼叫[IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)以取得錯誤中斷點繫結失敗的原因。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)

