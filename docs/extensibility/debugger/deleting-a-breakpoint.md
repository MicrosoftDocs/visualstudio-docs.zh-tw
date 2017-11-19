---
title: "刪除中斷點 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2789fd46942a9b54ca3d6efb082a6b21511969ca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="deleting-a-breakpoint"></a>刪除中斷點
以下描述刪除暫止中斷點時的處理程序：  
  
## <a name="deletion-process"></a>刪除程序  
 工作階段的偵錯管理員 (SDM) 呼叫[IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)從它的方法來移除暫止中斷點和所有繫結的中斷點繫結。  
  
> [!NOTE]
>  您也可以藉由呼叫刪除單一繫結的中斷點[IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)