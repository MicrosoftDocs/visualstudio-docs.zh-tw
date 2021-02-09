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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6ac3e8517ee99dcd52261eb87b6cee3954793d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895891"
---
# <a name="termination-and-detaching"></a>終止和卸離
下一節說明正常終止。

## <a name="discussion"></a>討論
 在 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 或 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 介面繼續之後，如果應用程式中沒有任何中斷點、例外狀況、執行階段錯誤或無限迴圈，則會執行正在調試的程式以完成。 此程式為正常終止。

 您必須傳送 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 來執行正常終止。 正常終止需要執行 [IDebugProgramDestroyEvent2：： GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) 方法。

## <a name="see-also"></a>另請參閱
- [建立自訂的調試引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)
