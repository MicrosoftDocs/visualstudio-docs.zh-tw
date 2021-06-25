---
title: 堆疊框架 |Microsoft Docs
description: 本文說明 Visual Studio 中偵錯工具架構中堆疊框架的定義和角色。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77b503afcc38ab9427e5268097655433007de5d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898548"
---
# <a name="stack-frames"></a>堆疊框架
在偵錯工具架構中， *堆疊框架*：

- 是堆疊的抽象概念，可提供執行緒的執行內容。 執行緒一律在函式內執行。 堆疊框架會保存函式的區域變數和其引數。 為了使用 Visual Studio 進行 debug，所要進行調試的語言或環境必須支援堆疊框架。

- 可以識別和描述本身，並且可以傳回相關聯的執行緒。 堆疊框架也可以傳回代表目前指令指標的程式碼內容，以及相關聯的檔和運算式評估內容。

- 的屬性會描述區域變數和引數的名稱、類型和值，而且會出現在不同的 IDE 偵錯工具視窗中。

- 是以 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 介面表示，通常是由偵錯工具引擎建立 (將) 或虛擬機器視為執行執行緒的結果。

## <a name="see-also"></a>另請參閱
- [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)
- [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)
- [Debug 引擎](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
