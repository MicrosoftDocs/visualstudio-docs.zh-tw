---
title: 除錯器概念 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ad8a450f9e79c1d44b8e098c8a00bb4b816e1af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738990"
---
# <a name="debugger-concepts"></a>除錯器概念
要構建 Visual Studio 調試包,您需要熟悉設計包時使用的體系結構概念。

## <a name="in-this-section"></a>本節內容
 [除錯工作階段](../../extensibility/debugger/debug-session.md)解釋會話在調試體系結構中的角色。

 [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md)以抽象和物理術語定義伺服器在調試體系結構方面的內容。

 [港口供應商](../../extensibility/debugger/port-suppliers.md)定義埠供應商在調試體系結構方面的內容。

 [連接埠](../../extensibility/debugger/ports.md)定義埠在調試體系結構方面是什麼。

 [流程](../../extensibility/debugger/processes.md)定義進程在調試體系結構方面是什麼。

 [程式節點](../../extensibility/debugger/program-nodes.md)定義程式節點的調試體系結構,包括它如何標識自身及其正在運行的進程。

 [排程](../../extensibility/debugger/programs.md)根據調試體系結構定義程式。

 [螺紋](../../extensibility/debugger/threads.md)定義線程在調試體系結構方面的特徵。

 [堆疊幀](../../extensibility/debugger/stack-frames.md)根據調試體系結構定義堆疊幀。 堆疊框架是提供線程執行上下文的堆疊的抽象。

 [模組](../../extensibility/debugger/modules.md)在調試體系結構方面,將模組定義為代碼的物理容器,如可執行檔或 DLL。

 [斷點](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)定義三種類型的斷點 - 掛起、綁定和錯誤 - 在除錯體系結構方面。

## <a name="related-sections"></a>相關章節
 [除錯器上下文](../../extensibility/debugger/debugger-contexts.md)說明除錯引擎 (DE) 如何在程式碼、文件和運算式評估上下文中同時執行。 描述三個上下文中的每一個與它相關的位置、位置或評估。

 [除錯器元件](../../extensibility/debugger/debugger-components.md)提供可視化工作室調試元件的概述,其中包括調試引擎 (DE)、運算式賦值器 (EE) 和符號處理程式 (SH)。

 [除錯工作](../../extensibility/debugger/debugging-tasks.md)包含指向各種除錯任務的連結,例如啟動程式和評估運算式。
