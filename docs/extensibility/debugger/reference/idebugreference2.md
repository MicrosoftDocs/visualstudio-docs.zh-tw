---
title: IDebugReference2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c6e68785640e68aa6fe4641528ca2f96d3c8406
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54978278"
---
# <a name="idebugreference2"></a>IDebugReference2
此介面代表堆疊框架屬性或其他某個屬性的參考。  
  
> [!NOTE]
>  `IDebugReference2` 保留供未來使用，和所有其方法應該傳回`E_NOTIMPL`。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 DE 會實作這個介面來代表特定類型的值的參考。 例如，值可以是數值，運算式評估，用來顯示記憶體或暫存器和其值的清單的記憶體內容的結果。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)來取得這個介面。 [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)並[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)也會傳回此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugReference2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|取得[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)描述此參考的結構。|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|設定此參考，從字串的值。|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|設定從另一個參考這個參考值。|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|列舉此參考的子系。|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|取得此參考的父代。|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|取得此參考的最高衍生性參考。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|取得這個參考是參考的記憶體位元組。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|取得這個參考中的記憶體內容。|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|取得大小，以位元組為單位，此參考。|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|設定此參考型別。|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|比較這個與另一個的參考。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這種使用 「 屬性 」 不應混淆與表示類別的成員變數雖然`IDebugReference2`可以表示這個實體。  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)表示的屬性，而`IDebugReference2`代表屬性時，通常是正在偵錯程式中的物件參考的參考。  
  
 屬性和參考的主要差異是物件的，屬性指的是物件的具名執行個體，而參考所參考的未命名的執行個體。 例如，屬性可能會由程式的堆積中的物件參考`"a.b"`。 另一個屬性可能會參考相同的物件為`"c.d"`。 參考這個屬性的方式要求`"a.b"`或`"c.d"`必須在範圍內。 這個相同的物件參考是無名稱;參考的物件可以是，只要該物件的記憶體有效。  
  
 `IDebugProperty2`介面可以視為具有名稱、 類型和地址的值。 `IDebugReference2`、 在其他另一方面，可以視為是型別和位址。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)