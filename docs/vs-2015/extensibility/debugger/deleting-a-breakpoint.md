---
title: 刪除中斷點 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42cd353c216c21d14c4f6592da809c72acdba664
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838995"
---
# <a name="deleting-a-breakpoint"></a>刪除中斷點
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

以下說明刪除暫止中斷點時的程式：  
  
## <a name="deletion-process"></a>刪除進程  
 會話 debug manager (SDM) 會呼叫 [IDebugPendingBreakpoint2：:D elete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) 方法，以移除暫止中斷點以及所有與其系結的系結中斷點。  
  
> [!NOTE]
> 單一系結中斷點也可以透過呼叫 [IDebugBoundBreakpoint2：:D elete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)來刪除。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
