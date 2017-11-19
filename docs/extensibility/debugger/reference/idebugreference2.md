---
title: "IDebugReference2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugReference2
helpviewer_keywords: IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27e880dbf5b602c1bd0b98c6ce5ccc2fdf88e37a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugreference2"></a>IDebugReference2
此介面代表堆疊框架屬性或某些其他屬性的參考。  
  
> [!NOTE]
>  `IDebugReference2`保留供未來使用，和其方法應該傳回所有`E_NOTIMPL`。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 實作這個介面來代表值的特定種類的參考。 例如，值可以是數值，運算式評估，則用來顯示的記憶體或暫存器及其值的清單的記憶體內容的結果。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)取得此介面。 [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)和[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)也會傳回此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugReference2`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|取得[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)說明這個參考的結構。|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|設定此參考，從字串值。|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|設定從另一個參考這個參考值。|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|列舉此參考的子系。|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|取得這個參考的父代。|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|取得這個參考的最具衍生性參考。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|取得這個參考所參考的記憶體位元組。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|取得這個參考中的記憶體內容。|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|取得大小，以位元組為單位，此參考。|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|設定此參考類型。|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|比較這個與另一個的參考。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這種使用 「 屬性 」 應不與表示類別的成員變數混淆，雖然`IDebugReference2`可以代表這個實體。  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)表示的屬性，而`IDebugReference2`代表屬性時，通常為偵錯程式中的物件參考的參考。  
  
 屬性與參考之間的主要差異在於，屬性是指物件的具名執行個體時的參考是指未命名的執行個體。 例如，屬性可能會由程式的堆積中的物件參考`"a.b"`。 另一個屬性可能會參考相同的物件做為`"c.d"`。 參考到這個屬性的方式要求`"a.b"`或`"c.d"`可能在範圍內。 這個相同的物件參考是無名稱;物件可以參考，只要該物件的記憶體有效。  
  
 `IDebugProperty2`介面可以視為具有名稱、 類型和位址的值。 `IDebugReference2`、 在其他另一方面，可以想成是型別和位址。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)