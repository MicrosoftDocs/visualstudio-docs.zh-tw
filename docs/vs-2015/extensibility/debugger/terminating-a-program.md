---
title: 終止程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f0b9ad248751af0885fa4edc0275be2ede5ddd9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421859"
---
# <a name="terminating-a-program"></a>終止程式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

以下是具有一個執行緒之單一程式終止的描述。  
  
## <a name="termination-process"></a>終止進程  
  
1. DE 會傳送具有有效[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)的[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) 。  
  
2. DE 會傳送具有有效[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)的[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 。  
  
   IDE 進入設計模式。 偵錯工具引擎或執行時間環境會呼叫 [IDebugPortNotify2：： RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) ，以從埠中移除程式。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
