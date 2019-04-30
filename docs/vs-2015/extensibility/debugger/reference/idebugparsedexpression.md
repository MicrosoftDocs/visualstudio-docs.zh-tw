---
title: IDebugParsedExpression | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4756a346cc059b1f80aba98439b993ac84f1136f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431411"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面會表示準備要評估的已剖析的運算式。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugParsedExpression : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 運算式評估工具會實作這個介面來代表剖析的運算式，可供評估。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)傳回此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugParsedExpression`。  
  
|方法|描述|  
|------------|-----------------|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|評估已剖析的運算式。|  
  
## <a name="remarks"></a>備註  
 當呼叫端是準備要評估的運算式時，它會呼叫[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)返回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ，包含評估的結果。 評估，然後評估，可讓剖析的運算式會評估多次剖析、 略過費時的程序的剖析運算式這兩個部分方法。  
  
## <a name="requirements"></a>需求  
 標頭： ee.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
