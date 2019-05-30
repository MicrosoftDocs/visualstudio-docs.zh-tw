---
title: 偵錯工作 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 774999dbdcb9eaf4a948364956ed95ab57e24d10
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345846"
---
# <a name="debug-tasks"></a>偵錯工作
偵錯程式，就必須啟動並偵錯引擎 (DE) 必須連接到它，否則 DE 必須附加至先前啟動的程式。 附加後，裝置必須產生特定啟動事件。 在回應中，偵錯封裝會嘗試繫結在 IDE 中設定的中斷點。 當程式叫用繫結的中斷點時，它會中止，並等待使用者輸入。

## <a name="in-this-section"></a>本節內容
 [安全性問題](../../extensibility/debugger/security-issues.md)討論偵錯程式所需的安全性步驟。

 [啟動程式](../../extensibility/debugger/launching-a-program.md)提供有關如何指定規定，它會呼叫作業系統啟動程式的逐步指示。

 [直接附加到程式](../../extensibility/debugger/attaching-directly-to-a-program.md)說明用來偵錯處理序已在執行中的程式的程序。

 [在啟動後傳送啟動事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)列出 DE 附加至程式，直到程式在其主要進入點，並且可供偵錯後，會發生的事件。

 [控制執行](../../extensibility/debugger/control-of-execution.md)說明如何 DE 通常會將傳送的進入點事件、 載入完成的事件或停止事件，視情況而定。

 [繫結中斷點](../../extensibility/debugger/binding-breakpoints.md)說明如何執行，如果使用者設定中斷點，IDE 會構成要求，並提示偵錯工作階段，來建立中斷點。

 [評估運算式](../../extensibility/debugger/evaluating-expressions.md)說明如何建立運算式以及評估運算式時，會發生什麼事。

 [以視覺化方式檢視和檢視資料](../../extensibility/debugger/visualizing-and-viewing-data.md)說明如何支援運算式評估工具 (EE) 的類型視覺化檢視和自訂檢視器。

## <a name="related-sections"></a>相關章節
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)描述主要的偵錯架構概念。

 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)提供 Visual Studio 偵錯元件，包括 DE、 EE 和符號處理常式 (SH) 的概觀。

 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)說明 DE 運作同時的程式碼、 文件，以及運算式評估內容內。 描述三個內容、 位置、 位置或評估與它相關的每個軸。

## <a name="see-also"></a>另請參閱
 [開始使用](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)