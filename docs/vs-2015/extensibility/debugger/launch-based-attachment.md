---
title: 以啟動為基礎的附件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09a6b39bef9ba6af098bf92d779a490e22492209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203158"
---
# <a name="launch-based-attachment"></a>啟動時附加
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

以啟動為基礎的程式附件是自動的。 當裝載程式的進程由 SDM 啟動時，以啟動為基礎的附件會遵循與手動附件方法類似的路徑。 如需詳細資訊，請參閱 [附加至程式](../../extensibility/debugger/attaching-to-the-program.md)。  
  
## <a name="the-attaching-process"></a>附加進程  
 主要差異在於 **附加** 呼叫之後的事件順序，如下所示：  
  
1. 將 **IDebugEngineCreateEvent2** 事件物件傳送至 SDM。 如需詳細資訊，請參閱傳送 [事件](../../extensibility/debugger/sending-events.md)。  
  
2. `IDebugProgram2::GetProgramId`在傳遞至**附加**方法的**IDebugProgram2**介面上呼叫方法。  
  
3. 傳送 **IDebugProgramCreateEvent2** 事件物件，以通知 SDM 已建立本機 **IDebugProgram2** 物件來代表要解除的程式。  
  
4. 傳送 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 事件物件來通知 SDM，為啟動的進程建立新的執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [傳送所需的事件](../../extensibility/debugger/sending-the-required-events.md)   
 [啟用要偵錯的程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
