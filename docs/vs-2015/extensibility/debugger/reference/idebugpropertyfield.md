---
title: IDebugPropertyField |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bad60a24c9120c1425a5d9041a32755feeb6e6c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65692151"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面會提供可讓您取得和設定屬性的功能。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 符號提供者會在執行 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)的相同物件上，執行這個介面。 這個介面是一個特製化，可支援類別上的屬性概念。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 如果[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)方法傳回，請使用[QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)從[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面取得這個介面 `FIELD_KIND_PROP` 。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 和 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 介面上的方法，這個介面也會執行下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|取得取得屬性的方法。|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|取得設定屬性的方法。|  
  
## <a name="remarks"></a>備註  
 屬性是 managed 程式碼的概念，並代表視為變數的方法。 屬性不存在於非受控 c + + 中。  
  
## <a name="requirements"></a>需求  
 標頭： sh. h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
