---
title: IDebugReturnValueEvent2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReturnValueEvent2
helpviewer_keywords:
- IDebugReturnValueEvent2
ms.assetid: 2daded43-e427-4fbb-a19e-f3834e3723af
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b3a6ece54b76d38891f99cc96afa52df72d7138a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65676410"
---
# <a name="idebugreturnvalueevent2"></a>IDebugReturnValueEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面是由偵錯工具引擎傳送， (在跳過或非函式之後，將) 還原為會話 debug manager (SDM) 。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugReturnValueEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 DE 會執行這個介面，以從已超出或超過的函式報告傳回值。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 來存取 `IDebugEvent2` 介面。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 「取消」會建立並傳送此事件物件，以報告函數的傳回值。 使用 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件，該函式會在附加至要進行偵錯工具的程式時提供。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法 `IDebugReturnValueEvent2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)|取得跳出函式時所傳回的值。|  
  
## <a name="remarks"></a>備註  
 函數所傳回的值可以藉由呼叫 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)來取得。 傳回的值會出現在 [自動 **變數] 視窗** 中。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
