---
title: IDebugEntryPointEvent2 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7bf5e35251012c12e89e9948f3b0e5f59b337ab3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799960"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

偵錯引擎 (DE) 執行使用者程式碼的第一個指令程式時，將此介面傳送工作階段的偵錯管理員 (SDM)。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 DE 會實作這個介面做為其正常作業的一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面的相同物件上。 使用 SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)若要存取`IDebugEvent2`介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 DE 建立，並傳送這個事件物件，當正在進行偵錯的程式已載入並準備好執行使用者程式碼的第一個指令。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## <a name="remarks"></a>備註  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)時執行的第一個指令程式會傳送。 例如，`IDebugEntryPoint2`程式即將執行的使用者時，會傳送`main`函式。  
  
 當傳送 DE `IDebugEntryPointEvent2`，目前的程式碼位置應該是在第一個指令的使用者程式碼，例如`main`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

