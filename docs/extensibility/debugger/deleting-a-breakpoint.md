---
title: 刪除中斷點 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b63fa7622b7dea4a6ad5c516547518911110a8ef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958036"
---
# <a name="deleting-a-breakpoint"></a>刪除中斷點
以下說明時刪除暫止中斷點的程序：  
  
## <a name="deletion-process"></a>刪除程序  
 工作階段的偵錯管理員 (SDM) 會呼叫[IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)從它的方法，以移除暫止中斷點及所有繫結的中斷點繫結。  
  
> [!NOTE]
>  您也可以藉由呼叫刪除單一繫結的中斷點[IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)