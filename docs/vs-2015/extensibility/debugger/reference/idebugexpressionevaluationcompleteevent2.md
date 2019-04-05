---
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 130d8cca16a8b2ae0074269058f831768db39e94
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940377"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面會傳送偵錯引擎 (DE) 工作階段的偵錯管理員 (SDM) 非同步運算式評估完成時。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugExpressionEvaluationCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 DE 實作這個介面來報告完成運算式評估的呼叫開始著手[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面的相同物件上。 使用 SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)若要存取`IDebugEvent2`介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 DE 建立，並傳送這個事件来報告的物件完成的運算式評估。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugExpressionEvaluationCompleteEvent2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|取得原始的運算式。|  
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|取得運算式評估的結果。|  
  
## <a name="remarks"></a>備註  
 DE 必須傳送這個事件中，評估是否成功，或不。  
  
 如果不成功，評估`DEBUG_PROPINFO_VALUE`並`DEBUG_PROPINFO_ATTRIB`中，未設定旗標[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)所傳回的結構[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) ( [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) DE 所建立物件並傳回`IDebugExpressionEvaluationCompleteEvent2`如果評估失敗的事件)。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
