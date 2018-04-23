---
title: IDebugContainerField |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4bee04d21e3181d4590f26b64c794164ab1a84b6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
此介面代表符號或其他符號或類型的容器類型。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 符號提供者會實作此介面實作在相同物件上[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。 此介面也是代表容器的所有介面的基底類別。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 在許多介面上的許多方法會傳回此介面。 因為這是所有容器的基底類別，更具特製化的介面可以從這個介面取得使用[QueryInterface](/cpp/atl/queryinterface)。 這類介面包括[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)， [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)， [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)，和[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了上[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|建立容器的欄位的列舉值。|  
  
## <a name="remarks"></a>備註  
 陣列 （容器的變數）、 （容器方法和變數） 的類別和方法 （在容器中的參數和區域變數） 都是容器的範例。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)