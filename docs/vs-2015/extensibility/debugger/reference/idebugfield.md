---
title: IDebugField |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5984e372574ddb104e90415870d3d79020066e3f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218279"
---
# <a name="idebugfield"></a>IDebugField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面表示的欄位，也就是符號或類型的描述。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 符號提供者會實作這個介面的基底類別的所有欄位。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面是基底類別的所有欄位。 傳回值為基礎[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)，此介面可能會傳回更具特製化的介面，藉由使用[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)。 此外，許多介面傳回`IDebugField`從各種方法的物件。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugField`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|取得相關類型的符號可顯示的資訊。|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|取得欄位的類型。|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|取得欄位的型別。|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|取得欄位的容器。|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|取得欄位的位址。|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|取得欄位中，以位元組為單位的大小。|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|取得擴充欄位的相關資訊。|  
|[Equal](../../../extensibility/debugger/reference/idebugfield-equal.md)|比較兩個欄位。|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|取得型別無關的符號或類型資訊。|  
  
## <a name="remarks"></a>備註  
 類型相當於 C 語言`typedef`。  
  
 在下列 c + + 語言範例中，`weather`是類別類型，並`sunny`和`stormy`符號：  
  
```cpp#  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 欄位代表符號還是類型可決定藉由呼叫[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)檢查[FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)結果。 如果`FIELD_KIND_TYPE`設定位元，欄位是一個型別，而且如果`FIELD_KIND_SYMBOL`設定位元，它是一種符號。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)

