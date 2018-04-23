---
title: IDebugPointerField |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 63ac5f4f7e357ba256d7a796654100480a34533a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpointerfield"></a>IDebugPointerField
此介面代表指標類型。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 符號提供者會實作這個介面來代表指標。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 使用[QueryInterface](/cpp/atl/queryinterface)獲得從這個介面[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)傳回`FIELD_TYPE_POINTER`。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了上`IDebugField`和`IDebugContainerField`介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)描述指標的目標。|  
  
## <a name="remarks"></a>備註  
 C/c + +，則該值為使用具有陣列標記法指標時，可以是容器。 例如，假設`char *pString`，`pString`的類型指標為`char`。 `pString[3]` 具有指標的容器類型`char`參考該容器的第四個項目。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)