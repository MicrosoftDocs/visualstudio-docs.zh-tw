---
title: 執行緒 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 028ad25495ba01d9763c8bec3bbb9c4480d72ff8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185364"
---
# <a name="threads"></a>Threads
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

就偵錯工具架構而言， **執行緒**：  
  
- 這是計算的基礎單位。 執行緒會依序在單一呼叫堆疊的內容中執行其指示，並從一個程式碼內容移至下一個。  
  
- 可以識別自己及其執行所在的程式，並且可以命名、暫止和繼續。 執行緒也可以列舉其相關聯的堆疊框架，而且在某些情況下，可以移至另一個堆疊框架。 如果有堆疊框架的內容，執行緒可以傳回其相關聯的邏輯執行緒（如果有的話）。 執行緒具有可在 IDE 的 [執行緒] 視窗中顯示的屬性，例如「暫止計數」。  
  
- 是以 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 介面表示，通常是由 debug 引擎建立 (將) 或虛擬機器作為執行程式的結果。  
  
## <a name="see-also"></a>另請參閱  
 [程式](../../extensibility/debugger/programs.md)   
 [堆疊框架](../../extensibility/debugger/stack-frames.md)   
 [Debug 引擎](../../extensibility/debugger/debug-engine.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [工作階段偵錯管理員](../../extensibility/debugger/session-debug-manager.md)
