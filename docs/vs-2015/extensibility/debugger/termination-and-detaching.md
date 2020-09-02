---
title: 終止和卸離 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d92fe88826baf19ba66b200990aee7797e91f87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176667"
---
# <a name="termination-and-detaching"></a>終止並中斷連結
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

以下說明正常終止。  
  
## <a name="discussion"></a>討論  
 在 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 或 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 介面繼續之後，如果應用程式中沒有任何中斷點、例外狀況、執行階段錯誤或無限迴圈，則會執行正在進行調試的程式以完成。 這是正常終止。  
  
 您必須傳送 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 來執行正常終止。 這需要執行 [IDebugProgramDestroyEvent2：： GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) 方法。  
  
## <a name="see-also"></a>另請參閱  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)
