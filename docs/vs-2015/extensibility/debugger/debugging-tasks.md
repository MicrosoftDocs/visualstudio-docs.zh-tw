---
title: 調試作業 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4a8a9879bce6d91448bb4f29b842328ab56bb97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200603"
---
# <a name="debugging-tasks"></a>偵錯工作
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

若要對程式進行程式設計，必須將它啟動，而且必須將 debug engine (DE) 必須附加到該程式，否則 DE 必須附加至先前啟動的程式。 附加之後，DE 必須產生特定的啟動事件。 在回應中，debug 封裝會嘗試系結 IDE 中設定的中斷點。 當程式到達系結的中斷點時，它會中止，並等候使用者輸入。  
  
## <a name="in-this-section"></a>本節內容  
 [安全性問題](../../extensibility/debugger/security-issues.md)  
 討論偵錯工具所需的安全性步驟。  
  
 [啟動程式](../../extensibility/debugger/launching-a-program.md)  
 提供逐步指示，說明如何指定 DE，以呼叫作業系統來啟動程式。  
  
 [直接附加至程式](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 描述在已執行的進程中用來對程式進行程式設計的進程。  
  
 [在啟動後傳送啟動事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 列出將取消附加至程式之後所發生的事件，直到程式進入其主要進入點，並且準備好進行偵錯工具為止。  
  
 [控制執行](../../extensibility/debugger/control-of-execution.md)  
 說明刪除通常如何傳送進入點事件、載入完成事件或停止事件（視情況而定）。  
  
 [繫結中斷點](../../extensibility/debugger/binding-breakpoints.md)  
 描述當使用者設定中斷點時，IDE 會會構成要求並提示 debug 會話建立中斷點。  
  
 [評估運算式](../../extensibility/debugger/evaluating-expressions.md)  
 說明如何建立運算式，以及評估運算式時會發生什麼事。  
  
 [視覺化及檢視資料](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 說明運算式評估工具 (EE) 如何支援型別視覺化程式和自訂檢視器。  
  
## <a name="related-sections"></a>相關章節  
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要的調試架構概念。  
  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)  
 概述 Visual Studio 的偵錯工具元件，其中包括 DE、EE 和 symbol 處理常式 (SH) 。  
  
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)  
 說明如何在程式碼、檔和運算式評估內容中同時操作 DE。 描述每個內容的相關位置、位置或評估。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
