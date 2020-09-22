---
title: IDebugManagedObject |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: be39e42de029b597d46fc775ef7df63c5d31c0c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838767"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面可讓運算式評估工具 (EE) 在實值類別實例上呼叫屬性或方法 (例如 `System.Decimal`) ，以及設定其值，而不需在所要進行的程式上呼叫 [評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) 。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugManagedObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 運算式評估工具會執行這個介面，以代表 managed 程式碼物件，例如變數。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 若要取得這個介面，請在代表實值類別實例的[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)上呼叫[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) 。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了繼承自 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)的方法之外，介面也會 `IDebugManagedObject` 公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|傳回代表 managed 程式碼物件的介面，以及可從中取得任何適當 managed 程式碼介面的介面。|  
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|將這個物件的值設定為指定之 managed 程式碼物件的值。|  
  
## <a name="remarks"></a>備註  
 運算式評估工具會使用這個介面將 managed 程式碼物件儲存在剖析樹狀結構中。  
  
## <a name="requirements"></a>需求  
 標頭： ee. h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
