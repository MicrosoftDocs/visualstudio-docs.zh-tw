---
title: IDebugManagedObject |Microsoft Docs
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
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eff42a7ba1b2fb3850e3751928d07cc3181d6fcd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783892"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此介面可讓運算式評估工具 (EE) 值的類別執行個體上呼叫屬性或方法 (例如`System.Decimal`)，並設定其值，而不會呼叫[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)正在偵錯的程式。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugManagedObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 運算式評估工具會實作這個介面來代表 managed 程式碼的物件，例如的變數。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 若要取得這個介面，請呼叫[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)上[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)表示實值類別的執行個體。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了繼承自方法[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)，則`IDebugManagedObject`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|傳回表示 managed 程式碼物件，而且可以從哪些任何適當 managed 程式碼取得介面的介面。|  
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|指定 managed 程式碼之物件的值來設定此物件的值。|  
  
## <a name="remarks"></a>備註  
 運算式評估工具會使用這個介面，剖析樹狀結構中儲存 managed 程式碼的物件。  
  
## <a name="requirements"></a>需求  
 標頭： ee.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)

