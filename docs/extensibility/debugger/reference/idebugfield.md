---
title: "IDebugField |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1e978ece2ecf56735dc538324b5c148f7f85b9bb
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="idebugfield"></a>IDebugField
此介面代表一個欄位，也就是符號或類型的描述。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 符號提供者會實作這個介面的基底類別的所有欄位。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面是基底類別的所有欄位。 根據傳回值[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)，此介面可能會傳回更具特製化的介面使用[QueryInterface](/cpp/atl/queryinterface)。 此外，許多介面傳回`IDebugField`各種方法的物件。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugField`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|取得可顯示的符號或類型的相關資訊。|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|取得欄位的類型。|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|取得欄位的類型。|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|取得欄位的容器。|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|取得欄位的位址。|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|取得欄位，以位元組為單位的大小。|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|取得擴充欄位的相關資訊。|  
|[等於](../../../extensibility/debugger/reference/idebugfield-equal.md)|比較兩個欄位。|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|取得與類型無關的相關資訊的符號或類型。|  
  
## <a name="remarks"></a>備註  
 型別就相當於 C 語言`typedef`。  
  
 在下列 c + + 語言的範例，`weather`類別型別和`sunny`和`stormy`符號：  
  
```cpp  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 欄位代表符號還是可以藉由呼叫決定類型[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)和檢查[FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)結果。 如果`FIELD_KIND_TYPE`位元會設為欄位類型，而且如果`FIELD_KIND_SYMBOL`會設定位元，它是一種符號。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
