---
title: "IDebugProperty2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2
helpviewer_keywords: IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45ad3a6c0d250136d0ab3e1becb088ea140b42e8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2"></a>IDebugProperty2
此介面代表堆疊框架屬性、 程式文件屬性或某些其他屬性。 屬性通常是運算式評估的結果。  
  
> [!NOTE]
>  這種使用 「 屬性 」 應不與表示類別的成員變數混淆，雖然`IDebugProperty2`可以代表這個實體。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 實作這個介面來代表特定種類的值。 例如，值可以是數值，運算式評估，則用來顯示的記憶體或暫存器及其值的清單的記憶體內容的結果。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)取得此介面，代表評估的結果。 `IDebugExpression2::EvaluateAsync`傳回此介面傳送[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) SDM，依序呼叫的介面[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)擷取屬性。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)傳回這個介面可提供相關聯的指令碼文件。  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)傳回此介面代表函式的傳回值。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)傳回此介面代表各種屬性，例如名稱或記憶體內容的程式。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)傳回此介面來代表本機變數之類的堆疊框架的各種屬性。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugProperty2`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|填入[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構描述的屬性。|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|從字串中設定屬性的值。|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|設定屬性的值，指定參考的值。|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|列舉屬性的子系。|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|傳回屬性的父代。|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|傳回描述屬性的最具衍生性屬性的屬性。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|傳回的記憶體位元組組成屬性的值。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|傳回屬性值的記憶體內容。|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|傳回的大小，以位元組為單位的屬性值。|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|傳回這個屬性值的參考。|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|傳回擴充的屬性的資訊。|  
  
## <a name="remarks"></a>備註  
 屬性所表示的`IDebugProperty2`介面，可視為具有名稱、 類型和位址的值。 整體而言，`IDebugProperty2`可以代表任何項目具有階層式結構，以父代和子節點。  
  
 屬性是通常是暫時性的持續時間只有只要目前的堆疊框架，例如。 另一方面，參考所表示的[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)介面、 持續時間，只要，該值會維持在記憶體中。  
  
 可以使用 IDE`IDebugProperty2`介面，可讓使用者瀏覽和修改在執行階段屬性。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)