---
title: 啟動為基礎的附件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 892518cc92286f9415e39c96b6ed2afa8eb0d792
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="launch-based-attachment"></a>啟動為基礎的附件
啟動為基礎的附件，程式會自動執行。 裝載程式的處理序啟動時由 SDM，啟動為基礎的附件遵循類似於手動附件方法的路徑。 如需資訊，請參閱[附加至程式](../../extensibility/debugger/attaching-to-the-program.md)。  
  
## <a name="the-attaching-process"></a>附加的處理程序  
 主要差異在於的下列事件順序**附加**呼叫，如下所示：  
  
1.  傳送**IDebugEngineCreateEvent2** SDM 事件物件。 如需詳細資訊，請參閱[傳送事件](../../extensibility/debugger/sending-events.md)。  
  
2.  呼叫`IDebugProgram2::GetProgramId`方法**IDebugProgram2**介面傳遞到**附加**方法。  
  
3.  傳送**IDebugProgramCreateEvent2**通知 SDM 事件物件的本機**IDebugProgram2**以 DE 代表程式建立物件。  
  
4.  傳送[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)通知 SDM 啟動之處理序會建立一個新的執行緒事件物件。  
  
## <a name="see-also"></a>另請參閱  
 [傳送所需的事件](../../extensibility/debugger/sending-the-required-events.md)   
 [啟用要偵錯的程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)