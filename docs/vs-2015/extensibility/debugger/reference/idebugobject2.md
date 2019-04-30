---
title: IDebugObject2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8855d27448501abec506e3b363b41e64133c07fa
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431657"
---
# <a name="idebugobject2"></a>IDebugObject2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面會提供物件的其他資訊。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 運算式評估工具會實作這個介面來提供支援的別名以及存取物件的相關資訊。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面可以使用，取得這個介面[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)。 此外， [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)傳回此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 上的方法除了[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面，`IDebugObject2`實作下列介面：  
  
|方法|描述|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|取得變數的欄位 （如果有的話），可能會支援這個物件所表示的屬性。|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|取得表示這個物件值的 managed 程式碼物件。|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|建立此物件的唯一識別碼，或傳回現有的別名。|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|如果有的話，請取得與這個物件相關聯的別名。|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|取得這個物件的型別。|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|判斷這個物件是否代表使用者資料。|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|判斷是否不再有效的編輯後繼續的狀態。<br /><br /> 自訂運算式評估工具不會實作這個方法 (它應該會一律傳回`E_NOTIMPL`)。|  
  
## <a name="remarks"></a>備註  
 請參閱[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)如需別名的討論。  
  
## <a name="requirements"></a>需求  
 標頭： ee.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
