---
title: IDebugObject2 |Microsoft Docs
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
ms.openlocfilehash: 979ede5601f1f31ca972bb9067b626954b1296f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695202"
---
# <a name="idebugobject2"></a>IDebugObject2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面會提供物件的其他相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 運算式評估工具會執行這個介面，以提供別名的支援，以及物件相關資訊的存取權。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面可以使用[QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)來取得這個介面。 此外， [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) 會傳回這個介面。  
  
## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法  
 除了 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 介面上的方法之外，介面也會 `IDebugObject2` 執行下列動作：  
  
|方法|描述|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|取得欄位或變數 (是否有任何可支援此物件所表示之屬性的) 。|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|取得代表此物件值的 managed 程式碼物件。|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|建立這個物件的唯一識別碼，或傳回現有的別名。|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|取得與此物件相關聯的別名（如果有的話）。|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|取得此物件的型別。|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|判斷此物件是否代表使用者資料。|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|判斷編輯後繼續狀態是否不再有效。<br /><br /> 自訂表格達式評估工具不會執行此方法 (它應該一律傳回 `E_NOTIMPL`) 。|  
  
## <a name="remarks"></a>備註  
 如需別名的討論，請參閱 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 。  
  
## <a name="requirements"></a>需求  
 標頭： ee. h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
