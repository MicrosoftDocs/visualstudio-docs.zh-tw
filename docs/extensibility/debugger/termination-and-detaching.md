---
title: 終止並卸離 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e5af218098f6d79cf6208c66b314c35d2471af15
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="termination-and-detaching"></a>終止並卸離
以下描述正常終止。  
  
## <a name="discussion"></a>討論  
 之後[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)或[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)介面持續發生，如果沒有中斷點、 例外狀況，執行階段錯誤或要進行偵錯應用程式中的無限迴圈偵錯程式會執行到完成為止。 這是正常終止。  
  
 您必須傳送[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)實作正常終止。 這需要實作[IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)