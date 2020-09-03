---
title: 執行緒 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712484"
---
# <a name="threads"></a>Threads
在偵錯工具架構中， *執行緒*：

- 這是計算的基礎單位。 執行緒會依序在單一呼叫堆疊的內容中執行其指示，並從一個程式碼內容移至下一個。

- 可以識別其本身以及它正在執行的程式。 可以命名、暫止和繼續執行緒。 執行緒也可以列舉其相關聯的堆疊框架，而且在某些情況下，可以移至另一個堆疊框架。 如果有堆疊框架的內容，執行緒可以傳回其相關聯的邏輯執行緒（如果有的話）。 執行緒具有可在 IDE 的 [ **執行緒** ] 視窗中顯示的屬性，例如「暫止計數」。

- 是以 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 介面表示，通常是由 debug 引擎建立 (將) 或虛擬機器作為執行程式的結果。

## <a name="see-also"></a>另請參閱
- [程式](../../extensibility/debugger/programs.md)
- [堆疊框架](../../extensibility/debugger/stack-frames.md)
- [Debug 引擎](../../extensibility/debugger/debug-engine.md)
- [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)
- [會話偵錯工具管理員](../../extensibility/debugger/session-debug-manager.md)
