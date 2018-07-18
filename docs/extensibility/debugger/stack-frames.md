---
title: 堆疊框架 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: feb2bc9d87486b6f83cf4b19ecec24c8c03edee5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127995"
---
# <a name="stack-frames"></a>堆疊框架
偵錯工具就架構而言，**堆疊框架**:  
  
-   是抽象的提供執行緒的執行內容堆疊。 執行緒一律會執行函式內。 堆疊框架會保留它的函式和引數的本機變數。 若要使用 Visual Studio 偵錯，語言或正在進行偵錯環境必須支援堆疊框架。  
  
-   可以同時識別並描述自己，並可傳回相關聯的執行緒。 堆疊框架時，也可以傳回代表目前指令指標，並將相關聯的文件的程式碼內容和運算式評估內容。  
  
-   具有的屬性的描述名稱、 類型和值的本機變數和引數，以及哪些各種 IDE 偵錯視窗中會出現。  
  
-   由[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)介面，通常由偵錯引擎 (DE) 或由於執行執行緒的虛擬機器所建立。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)