---
title: IDebugEnumField |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ea0297b32d89b274d8c19250b03256e050797f06
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugenumfield"></a>IDebugEnumField
此介面代表列舉型別。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 符號提供者會實作這個介面來代表列舉型別。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 使用[QueryInterface](/cpp/atl/queryinterface)獲得從這個介面[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)傳回`FIELD_TYPE_ENUM`。  
  
## <a name="methods-in-vtable-order"></a>依照 VTable 順序的方法  
 除了上`IDebugField`和`IDebugContainerField`介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)描述這個列舉類型的名稱。|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|傳回與指定的值相關聯的列舉常數的名稱。|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|傳回與指定的列舉常數名稱相關聯的值|  
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|傳回具有指定的列舉常數的名稱，但略過的案例相關聯的值。|  
  
## <a name="remarks"></a>備註  
 它會實際繫結至的位置基礎符號[繫結](../../../extensibility/debugger/reference/idebugbinder-bind.md)。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [繫結](../../../extensibility/debugger/reference/idebugbinder-bind.md)