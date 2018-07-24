---
title: 偵錯工具概念 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e38c743ce7170e0842a3430c7b2aa190df94782b
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203802"
---
# <a name="debugger-concepts"></a>偵錯工具概念
若要建置 Visual Studio 偵錯封裝，您需要先熟悉中設計封裝所使用的架構概念。  
  
## <a name="in-this-section"></a>本節內容  
 [偵錯工作階段](../../extensibility/debugger/debug-session.md)  
 說明工作階段的偵錯的架構中的角色。  
  
 [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 定義哪一部伺服器是以偵錯架構，同時為 abstract 和實體的條款。  
  
 [連接埠提供者](../../extensibility/debugger/port-suppliers.md)  
 定義連接埠提供者是以偵錯架構。  
  
 [連接埠](../../extensibility/debugger/ports.md)  
 定義哪些連接埠是以偵錯架構。  
  
 [處理序](../../extensibility/debugger/processes.md)  
 定義哪個處理程序是以偵錯架構。  
  
 [程式節點](../../extensibility/debugger/program-nodes.md)  
 定義以偵錯架構，包括如何，它能識別本身和它正在中執行的程序的程式節點。  
  
 [程式](../../extensibility/debugger/programs.md)  
 定義偵錯架構方面的程式。  
  
 [執行緒](../../extensibility/debugger/threads.md)  
 定義偵錯架構方面的執行緒的特性。  
  
 [堆疊框架](../../extensibility/debugger/stack-frames.md)  
 定義偵錯架構方面的堆疊框架。 堆疊框架是堆疊提供執行緒的執行內容的抽象概念。  
  
 [模組](../../extensibility/debugger/modules.md)  
 定義模組，以進行架構，為實體容器的程式碼，例如可執行檔或 DLL 的偵錯。  
  
 [中斷點](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 定義三種中斷點類型 — 暫止、 繫結和錯誤，以偵錯架構。  
  
## <a name="related-sections"></a>相關章節  
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)  
 說明偵錯引擎 (DE) 的運作方式同時在程式碼、 文件和運算式評估內容。 描述三個內容、 位置、 位置或評估與它相關的每個軸。  
  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)  
 提供 Visual Studio 偵錯元件，包括偵錯引擎 (DE)、 運算式評估工具 (EE)，以及符號處理常式 (SH) 的概觀。  
  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)  
 包含各種不同的偵錯工作，例如啟動程式，以及評估運算式的連結。