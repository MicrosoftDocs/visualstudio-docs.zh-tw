---
title: IDebugField |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8bc18204d3cbe20635ab0680a50b4d1555dce2ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690298"
---
# <a name="idebugfield"></a>IDebugField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面代表一個欄位，也就是符號或型別的描述。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 符號提供者會將這個介面實作為所有欄位的基類。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 此介面是所有欄位的基類。 根據 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)的傳回值，此介面可能會使用 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)傳回更特製化的介面。 此外，許多介面都會 `IDebugField` 從不同的方法傳回物件。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法 `IDebugField` 。  
  
|方法|描述|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|取得符號或類型的可顯示資訊。|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|取得欄位的種類。|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|取得欄位的類型。|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|取得欄位的容器。|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|取得欄位的位址。|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|取得欄位的大小（以位元組為單位）。|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|取得欄位的延伸資訊。|  
|[等於](../../../extensibility/debugger/reference/idebugfield-equal.md)|比較兩個欄位。|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|取得與符號或類型無關的類型相關資訊。|  
  
## <a name="remarks"></a>備註  
 類型相當於 C 語言 `typedef` 。  
  
 在下列 c + + 語言範例中， `weather` 是類別類型，而且 `sunny` 和 `stormy` 都是符號：  
  
```cpp#  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 欄位是否代表符號或類型，可以藉由呼叫 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 和檢查 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) 結果來決定。 如果 `FIELD_KIND_TYPE` 設定位，則欄位為類型，如果 `FIELD_KIND_SYMBOL` 設定位，則為符號。  
  
## <a name="requirements"></a>需求  
 標頭： sh. h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
