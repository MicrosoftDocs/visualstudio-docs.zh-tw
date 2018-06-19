---
title: 作業模式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 72ae5a36f9f0547635872f5c8ebe30f2f3c53d5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105563"
---
# <a name="operational-modes"></a>作業模式
有三種模式中的 IDE 可以操作，如下所示：  
  
-   [設計模式](#vsconoperationalmodesanchor1)  
  
-   [執行模式](#vsconoperationalmodesanchor2)  
  
-   [中斷模式](#vsconoperationalmodesanchor3)  
  
 您的自訂偵錯引擎 (DE) 這些模式之間的轉換方式是實作決策會要求您先熟悉轉換機制。 DE 可能或可能會直接實作這些模式。 這些模式才真正偵錯封裝模式切換使用者動作或事件來自 DE 為基礎。 比方說，從執行模式為中斷模式轉換是從 DE 停止事件所引發。 從中斷模式或步驟模式執行的轉換被啟動使用者執行步驟或 Execute 之類的作業。 如需 DE 轉換的詳細資訊，請參閱[控制執行](../../extensibility/debugger/control-of-execution.md)。  
  
##  <a name="vsconoperationalmodesanchor1"></a> 設計模式  
 設計模式是 nonrunning 狀態的偵錯 Visual Studio，在這段期間您可以設定偵錯應用程式中的功能。  
  
 只有少數偵錯期間設計模式中所使用的功能。 開發人員可以選擇設定中斷點，或者建立監看式運算式。 DE 永遠不會載入或 IDE 處於設計模式時呼叫。 DE 互動期間執行和中斷模式中才會進行。  
  
##  <a name="vsconoperationalmodesanchor2"></a> 執行模式  
 在 IDE 中的偵錯工作階段中執行程式時，就會發生執行的模式。 應用程式執行之前終止，直到遇到中斷點時，或擲回例外狀況。 當應用程式執行的終止時，進入設計模式的 DE 轉換。 當叫用中斷點或發生例外狀況時，DE 會轉換到中斷模式。  
  
##  <a name="vsconoperationalmodesanchor3"></a> 中斷模式  
 暫停執行的偵錯程式時，就會發生中斷模式。 中斷模式時中斷的應用程式的快照集提供開發人員，並可讓開發人員分析應用程式的狀態，並變更應用程式執行的方式。 開發人員可以檢視和編輯程式碼、 檢查或修改資料、 重新啟動應用程式，結束執行，或繼續執行，從相同的點。  
  
 當 DE 傳送同步停止事件，會輸入中斷模式。 同步停止事件，也稱為停止事件通知工作階段的偵錯管理員 (SDM) 與正在偵錯應用程式已停止執行程式碼的 IDE。 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)和[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)介面是停止事件的範例。  
  
 正在停止事件會繼續由呼叫下列方法，轉換偵錯工具中斷模式下執行，或逐步執行模式的其中一個：  
  
-   [執行](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> 步驟模式  
 逐步執行下一行程式碼，或執行、 不進入或離函式的程式時，就會發生步驟模式。 呼叫的方法來執行步驟[步驟](../../extensibility/debugger/reference/idebugprocess3-step.md)。 此方法需要`DWORD`s 指定[STEPUNIT](../../extensibility/debugger/reference/stepunit.md)和[STEPKIND](../../extensibility/debugger/reference/stepkind.md)列舉型別做為輸入參數。  
  
 當程式成功地逐步執行至下一行程式碼或函式，或執行至游標處，或設定之中斷點時，DE 會自動轉換回中斷模式。  
  
## <a name="see-also"></a>另請參閱  
 [控制執行](../../extensibility/debugger/control-of-execution.md)