---
title: IDebugThreadDestroyEvent2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThreadDestroyEvent2
helpviewer_keywords:
- IDebugThreadDestroyEvent2
ms.assetid: fca3f603-9432-457b-9ddd-8b0ec17da046
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 837fba4afa64c0627fcac7ab9d904ef41c00e27a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704803"
---
# <a name="idebugthreaddestroyevent2"></a>IDebugThreadDestroyEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面是由偵錯工具引擎傳送 (當執行緒已執行完成時，將) 還原為會話 debug manager (SDM) 。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugThreadDestroyEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 DE 會執行此介面來報告執行緒已結束。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 來存取 `IDebugEvent2` 介面。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 DE 會建立並傳送此事件物件，以報告執行緒已結束。 使用 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件，該函式會在附加至要進行偵錯工具的程式時提供。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法 `IDebugThreadDestroyEvent2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[GetExitCode](../../../extensibility/debugger/reference/idebugthreaddestroyevent2-getexitcode.md)|取得執行緒的結束代碼。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 使用此事件來更新 [ **執行緒** ] 視窗。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
