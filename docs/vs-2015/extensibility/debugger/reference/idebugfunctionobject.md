---
title: IDebugFunctionObject |Microsoft Docs
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
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6c9d7e8e2d5cd9e8bbe190ac25c88e30f53fb0ec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285970"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面會表示函式。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugFunctionObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 運算式評估工具會實作這個介面來表示函式。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面是特製化[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面，並使用取得[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)上`IDebugObject`介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了繼承自方法[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)，則`IDebugFunctionObject`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|建立基本資料物件。|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|建立使用建構函式的物件。|  
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|使用沒有建構函式建立物件。|  
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|建立的陣列物件。|  
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|建立字串物件。|  
|[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|呼叫函式，並傳回產生的值當做物件。|  
  
## <a name="remarks"></a>備註  
 此介面可讓運算式評估工具，來代表剖析樹狀結構中的函式。 `Create`這個介面中的方法用來建構物件，代表方法的輸入的參數。 然後藉由呼叫執行函式[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)方法，這個方法會傳回代表函式的傳回值的物件。  
  
## <a name="requirements"></a>需求  
 標頭： ee.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

