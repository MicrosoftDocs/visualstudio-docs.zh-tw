---
title: IDebugPropertyField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 017ab4116654bb341162e46352dcb16b85528a74
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54995904"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
這個介面會提供允許取得和設定屬性的函式。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 符號提供者所實作的相同物件上實作這個介面[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)。 這個介面是特製化的類別支援屬性的概念。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 使用[QueryInterface](/cpp/atl/queryinterface)若要取得從這個介面[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)方法會傳回`FIELD_KIND_PROP`。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 上的方法除了[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)並[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|取得取得屬性的方法。|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|取得設定屬性的方法。|  
  
## <a name="remarks"></a>備註  
 屬性是 managed 程式碼的概念，因此表示都會視為變數的方法。 屬性不存在於非受控 c + +。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)