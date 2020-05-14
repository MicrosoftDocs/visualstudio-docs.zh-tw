---
title: 除錯任務 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d41f53ab1392ea3c31908faf65a871fa100fbb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738965"
---
# <a name="debug-tasks"></a>除錯工作
要調試程式,必須啟動該程式,並且必須將調試引擎 (DE) 附加到它,否則 DE 必須附加到以前啟動的程式。 附加後,DE 必須生成某些啟動事件。 作為回應,調試包嘗試綁定在IDE中設置的斷點。 當程序達到綁定斷點時,它將停止並等待使用者輸入。

## <a name="in-this-section"></a>本節內容
 [安全問題](../../extensibility/debugger/security-issues.md)討論調試程式所需的安全步驟。

 [啟動程式](../../extensibility/debugger/launching-a-program.md)提供有關如何指定 DE 的分步說明,該 DE 調用作業系統啟動程式。

 [直接附加到程式](../../extensibility/debugger/attaching-directly-to-a-program.md)描述用於在已運行的進程中調試程序的過程。

 [啟動後傳送啟動事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)列出 DE 附加到程式後發生的事件,直到程式位於其主要入口點並準備好進行調試。

 [執行控制](../../extensibility/debugger/control-of-execution.md)說明 DE 通常如何根據具體情況發送入口點事件、負載完成事件或停止事件。

 [繫結斷點](../../extensibility/debugger/binding-breakpoints.md)描述如果用戶設置斷點,IDE 如何制定請求並提示調試會話創建斷點。

 [計算運算式](../../extensibility/debugger/evaluating-expressions.md)說明如何創建表達式以及計算表達式時會發生什麼情況。

 [視覺化與檢視資料](../../extensibility/debugger/visualizing-and-viewing-data.md)說明運算式賦值器 (EE) 如何支援類型視覺化器和自訂檢視器。

## <a name="related-sections"></a>相關章節
 [除錯器概念](../../extensibility/debugger/debugger-concepts.md)描述主要的調試體系結構概念。

 [除錯器元件](../../extensibility/debugger/debugger-components.md)提供 Visual Studio 除錯元件的概述,其中包括 DE、EE 和符號處理程式 (SH)。

 [除錯器上下文](../../extensibility/debugger/debugger-contexts.md)說明 DE 如何在代碼、文檔和運算內容中同時運行。 描述三個上下文中的每一個與它相關的位置、位置或評估。

## <a name="see-also"></a>另請參閱
 [開始使用](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
