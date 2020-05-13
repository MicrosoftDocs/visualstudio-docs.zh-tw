---
title: 線程 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ed5c06e0c42dac1f0539cc2c7c5886d95b23ae1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712484"
---
# <a name="threads"></a>Threads
在除錯器架構結構中,*線程*:

- 是計算的基本單位。 線程在單個調用堆疊的上下文中按順序執行其指令,從一個代碼上下文移動到下一個代碼上下文。

- 可以標識自身及其正在運行的程式。 可以命名、掛起和恢復線程。 線程還可以枚舉其關聯的堆疊幀,在某些情況下,可以移動到另一個堆疊幀。 給定堆疊幀的上下文,線程可以返回其關聯的邏輯線程(如果有)。 線程具有可在 IDE**的「線程」** 視窗中顯示的屬性(如掛起計數)。

- 由[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)介面表示,通常由調試引擎 (DE) 或虛擬機作為執行程序的結果創建。

## <a name="see-also"></a>另請參閱
- [Programs](../../extensibility/debugger/programs.md)
- [堆疊幀](../../extensibility/debugger/stack-frames.md)
- [偵錯引擎](../../extensibility/debugger/debug-engine.md)
- [除錯器概念](../../extensibility/debugger/debugger-concepts.md)
- [工作階段除錯管理員](../../extensibility/debugger/session-debug-manager.md)
