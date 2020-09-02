---
title: IDebugEnumField |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac993e3a4676f1c84a193ddbf6e9a3b5bc8fa235
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65676510"
---
# <a name="idebugenumfield"></a>IDebugEnumField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面代表列舉型別。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 符號提供者會執行此介面來代表列舉。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 如果[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)傳回，請使用[QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)從[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面取得這個介面 `FIELD_TYPE_ENUM` 。  
  
## <a name="methods-in-vtable-order"></a>採用 VTable 順序的方法  
 除了和介面上的方法 `IDebugField` `IDebugContainerField` ，這個介面也會執行下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|傳回描述此列舉型別名稱的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 。|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|傳回與指定值相關聯之列舉常數的名稱。|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|傳回與指定的列舉常數名稱相關聯的值。|  
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|傳回與指定的列舉常數名稱相關聯的值，但忽略大小寫。|  
  
## <a name="remarks"></a>備註  
 它是實際系結至具有系結之位置的基礎[符號。](../../../extensibility/debugger/reference/idebugbinder-bind.md)  
  
## <a name="requirements"></a>需求  
 標頭： sh. h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [繫結](../../../extensibility/debugger/reference/idebugbinder-bind.md)
