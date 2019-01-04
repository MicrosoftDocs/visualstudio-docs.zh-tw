---
title: 作業模式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 158eca797c13ca7889ea4d7cf2e5d811783e997e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923675"
---
# <a name="operational-modes"></a>作業模式
有三種模式，在其中 IDE 可以操作，如下所示：  
  
- [設計模式](#vsconoperationalmodesanchor1)  
  
- [執行模式](#vsconoperationalmodesanchor2)  
  
- [中斷模式](#vsconoperationalmodesanchor3)  
  
  您自訂的偵錯引擎 (DE) 這些模式之間的轉換方式是要求您先熟悉轉換機制的實作決策。 DE 可能會或可能不直接實作這些模式。 這些模式其實是偵錯封裝模式切換根據使用者動作或來自德國的事件。 比方說，從執行模式中以中斷模式轉換為啟動停止事件來自 DE。 從 [中斷] 來執行模式或步驟模式轉換被啟動使用者執行步驟或 Execute 等作業。 如需 DE 轉換的詳細資訊，請參閱[控制執行](../../extensibility/debugger/control-of-execution.md)。  
  
##  <a name="vsconoperationalmodesanchor1"></a> 設計模式  
 設計模式是 nonrunning 狀態的 Visual Studio 偵錯，在這段期間您可以設定偵錯應用程式中的功能。  
  
 只有幾個偵錯期間設計模式中所使用的功能。 開發人員可以選擇設定中斷點，或建立監看式運算式。 DE 永遠不會載入或 IDE 處於設計模式時呼叫。 DE 互動執行和中斷模式期間，會發生。  
  
##  <a name="vsconoperationalmodesanchor2"></a> 執行模式  
 在 IDE 中的偵錯工作階段中執行的程式時，就會發生執行的模式。 應用程式執行之前終止，直到遇到中斷點時，或擲回例外狀況。 應用程式執行時終止，預設會轉換成設計模式。 當叫用中斷點或發生例外狀況時，預設會轉換成中斷模式。  
  
##  <a name="vsconoperationalmodesanchor3"></a> 中斷模式  
 暫停偵錯的程式執行時，就會發生中斷模式。 中斷模式提供開發人員的中斷時間的應用程式的快照集，並可讓開發人員分析的應用程式的狀態，並變更應用程式執行的方式。 開發人員可以檢視和編輯程式碼、 檢查或修改資料、 重新啟動應用程式，結束執行，或繼續執行，從相同的點。  
  
 DE 傳送同步停止 」 事件時，會輸入中斷模式。 同步的停止事件，也稱為停止事件會通知工作階段的偵錯管理員 (SDM) 和正在偵錯應用程式已停止執行程式碼的 IDE。 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)並[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)介面是停止事件的範例。  
  
 正在停止事件會繼續藉由呼叫下列方法，轉換偵錯工具中斷模式下執行，或逐步執行模式的其中一個：  
  
-   [Execute](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> 步驟模式  
 當程式逐步執行至下一行程式碼，或為、 不進入或離函式時，就會發生步驟模式。 步驟執行所呼叫方法[步驟](../../extensibility/debugger/reference/idebugprocess3-step.md)。 此方法需要`DWORD`指定的 s [STEPUNIT](../../extensibility/debugger/reference/stepunit.md)並[STEPKIND](../../extensibility/debugger/reference/stepkind.md)列舉型別做為輸入參數。  
  
 當程式成功地逐步執行至下一行程式碼或函式，或執行至游標處，或要設定中斷點時，DE 就會自動轉換回中斷模式中。  
  
## <a name="see-also"></a>另請參閱  
 [控制執行](../../extensibility/debugger/control-of-execution.md)