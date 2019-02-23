---
title: 終止並中斷連結 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a727f30f6070b44e16dbc4206ac56e0224ff3d67
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682163"
---
# <a name="termination-and-detaching"></a>終止並中斷連結
下節說明正常終止。

## <a name="discussion"></a>討論
 在後[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)或是[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)介面持續發生，如果沒有任何中斷點、 例外狀況、 執行階段錯誤或要進行偵錯應用程式中的無限迴圈正在進行偵錯程式會執行到完成為止。 此程序已正常終止。

 您必須傳送[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)實作正常終止。 正常終止需要執行[IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)方法。

## <a name="see-also"></a>另請參閱
- [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)