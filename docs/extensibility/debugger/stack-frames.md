---
title: 堆疊幀 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ea79ad199e20afeb5d2bf1ca6a3cf881c6d51c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712848"
---
# <a name="stack-frames"></a>堆疊幀
在除錯器結構中,*堆疊*

- 是提供線程執行上下文的堆疊的抽象。 線程始終在函數中執行。 堆疊幀保存函數的局部變數及其參數。 為了使用 Visual Studio 進行調試,正在調試的語言或環境必須支援堆疊幀。

- 可以標識和描述自身,也可以返回關聯的線程。 堆疊幀還可以返回表示當前指令指標以及關聯的文檔和表達式計算上下文的代碼上下文。

- 具有描述局部變數和參數的名稱、類型和值的屬性,這些屬性將顯示在各種 IDE 調試視窗中。

- 由[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)介面表示,該介面通常由調試引擎 (DE) 或虛擬機器創建,作為執行線程的結果。

## <a name="see-also"></a>另請參閱
- [除錯器上下文](../../extensibility/debugger/debugger-contexts.md)
- [除錯器概念](../../extensibility/debugger/debugger-concepts.md)
- [偵錯引擎](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
