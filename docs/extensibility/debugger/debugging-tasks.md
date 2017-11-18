---
title: "偵錯工作 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8bd22d71753a8bf86adbe2b437407481388c48d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-tasks"></a>偵錯工作
偵錯程式，它必須啟動並偵錯引擎 (DE) 必須連接到它，否則 DE 必須附加至先前啟動程式。 在附加之後，DE 必須產生特定的啟動事件。 在回應時，偵錯封裝嘗試繫結在 IDE 中設定的中斷點。 當程式叫用繫結的中斷點時，它會中止，並等待使用者輸入。  
  
## <a name="in-this-section"></a>本章節內容  
 [安全性問題](../../extensibility/debugger/security-issues.md)  
 討論偵錯程式所需的安全性步驟。  
  
 [啟動程式](../../extensibility/debugger/launching-a-program.md)  
 提供逐步指示如何指定 DE，它會呼叫您要啟動程式的作業系統。  
  
 [直接附加至程式](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 描述用來偵錯的程式已執行的處理序中的程序。  
  
 [在啟動後傳送啟動事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 列出 DE 附加至該程式，直到程式位於其主要進入點，並且準備好進行偵錯之後，會發生的事件。  
  
 [控制執行](../../extensibility/debugger/control-of-execution.md)  
 說明如何 DE 通常傳送進入點事件、 載入完成的事件或停止事件，視情況而定。  
  
 [繫結中斷點](../../extensibility/debugger/binding-breakpoints.md)  
 描述如何執行，如果使用者設定中斷點，IDE 會構成要求，並提示偵錯工作階段來建立中斷點。  
  
 [評估運算式](../../extensibility/debugger/evaluating-expressions.md)  
 說明如何建立運算式，以及在評估運算式時，會發生什麼事。  
  
 [視覺化及檢視資料](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 說明如何支援由運算式評估工具 (EE) 的類型視覺化檢視和自訂檢視器。  
  
## <a name="related-sections"></a>相關章節  
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要的偵錯架構概念。  
  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)  
 提供 Visual Studio 偵錯元件，包括 DE、 EE，以及符號處理常式 (SH) 的概觀。  
  
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)  
 說明如何 DE 同時中運作的程式碼、 文件和運算式評估內容。 描述三個內容、 位置、 位置或評估適用於它的每個軸。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)