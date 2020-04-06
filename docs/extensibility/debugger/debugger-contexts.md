---
title: 除錯器上下文 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56825fe299147e60c5ed9dfcefa491a427ab59e4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738970"
---
# <a name="debugger-contexts"></a>除錯器上下文
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]除錯中,除錯引擎 (DE) 在幾個不同的上下文中同時運行,如下所示:

- 代碼上下文,它描述程式執行流中的當前位置。

- 文件上下文或位置,用於描述源文檔中的當前位置。

- 表達式計算上下文,它描述將進行表達式計算的上下文。

## <a name="in-this-section"></a>本節內容
 [代碼內容](../../extensibility/debugger/code-context.md)將代碼上下文作為當今運行時體系結構中程式指令流中的地址討論,而非傳統語言則不由指令表示,但使用其他一些方法。

 [文件位置](../../extensibility/debugger/document-position.md)通過在源檔中的位置(如IDE已知)的抽象來定義Visual Studio調試中的文檔位置。

 [文件內容](../../extensibility/debugger/document-context.md)討論視覺化工作室調試中相對於源檔表示的文檔上下文。 還討論了符號處理程式如何將代碼上下文映射到文檔上下文。

 [運算式運算內容](../../extensibility/debugger/expression-evaluation-context.md)提供有關可視化工作室中的表達式評估上下文的資訊。 例如,與堆疊框架關聯的表達式計算上下文提供用於評估局部變數、方法參數和類成員的上下文。

## <a name="related-sections"></a>相關章節
 [除錯概念](../../extensibility/debugger/debugger-concepts.md)描述主要的調試體系結構概念。

 [除錯元件](../../extensibility/debugger/debugger-components.md)提供 Visual Studio 除錯元件的概述,其中包括除錯引擎 (DE)、運算式賦值器 (EE) 和符號處理程式 (SH)。

 [除錯工作](../../extensibility/debugger/debugging-tasks.md)包含指向各種除錯任務的連結,例如啟動程式和評估運算式。
