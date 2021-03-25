---
title: 終止和卸離 |Microsoft Docs
description: 正常終止表示正在進行調試的程式會執行到完成，而且沒有中斷點、例外狀況、執行階段錯誤或無限迴圈。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8662809b50dbfec3046af1d0d6b6fa151c3a33e0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057828"
---
# <a name="termination-and-detaching"></a>終止和卸離
下一節說明正常終止。

## <a name="discussion"></a>討論
 在 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 或 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 介面繼續之後，如果應用程式中沒有任何中斷點、例外狀況、執行階段錯誤或無限迴圈，則會執行正在調試的程式以完成。 此程式為正常終止。

 您必須傳送 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 來執行正常終止。 正常終止需要執行 [IDebugProgramDestroyEvent2：： GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) 方法。

## <a name="see-also"></a>另請參閱
- [建立自訂的調試引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)
