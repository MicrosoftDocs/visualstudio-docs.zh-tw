---
title: IDebugEntryPointEvent2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ed45b6d0166a92e9547b7ad76e189108cd2b5e02
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
偵錯引擎 (DE) 時即將執行的使用者程式碼的第一個指令程式，將此介面傳送至工作階段的偵錯管理員 (SDM)。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 實作這個介面做為其正常作業的一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件。 SDM 使用[QueryInterface](/cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 建立和傳送此事件的物件時進行偵錯的程式已載入並準備好執行使用者程式碼的第一個指令。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## <a name="remarks"></a>備註  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)時即將執行的第一個指令程式會傳送。 例如，`IDebugEntryPoint2`程式即將執行的使用者時傳送`main`函式。  
  
 當傳送 DE `IDebugEntryPointEvent2`，目前的程式碼位置應該在第一個指令的使用者程式碼，例如`main`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)