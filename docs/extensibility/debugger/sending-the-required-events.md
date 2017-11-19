---
title: "傳送所需的事件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30a5b1150d44c138465db36da2b032b71f075397
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="sending-the-required-events"></a>傳送所需的事件
使用此程序所需的事件傳送。  
  
## <a name="process-for-sending-required-events"></a>必要的事件傳送程序  
 下列事件是必要項，這個順序，當建立偵錯引擎 (DE) 和附加至程式中：  
  
1.  傳送[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)事件工作階段的偵錯管理員 DE 初始化偵錯的處理序中的一個或多個程式時 (SDM) 物件。  
  
2.  當要偵錯程式連接至時，傳送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) SDM 事件物件。 此事件可能會停止事件，根據您引擎的設計。  
  
3.  如果程式附加至處理序啟動時，傳送[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)通知新執行緒的 IDE SDM 事件物件。 此事件可能會停止事件，根據您引擎的設計。  
  
4.  傳送[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) SDM 完成的載入或附加至該程式完成時進行偵錯程式時的事件物件。 這個事件必須是停止事件。  
  
5.  若要偵錯應用程式啟動時，傳送[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)事件 SDM 時執行程式碼的執行階段架構中的第一個指令的物件。 這個事件永遠是停止事件。 逐步執行偵錯工作階段，IDE 就會停止此事件。  
  
> [!NOTE]
>  許多語言的程式碼開頭使用全域初始設定式或外部的先行編譯的函式 （從 CRT 程式庫或 _Main）。 如果您正在偵錯的程式語言，包含這些類型的初始項目點之前的項目，然後執行這個程式碼並不會傳送項目點事件時的使用者進入點，例如**主要**或`WinMain`，已達到。  
  
## <a name="see-also"></a>另請參閱  
 [啟用要偵錯的程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)