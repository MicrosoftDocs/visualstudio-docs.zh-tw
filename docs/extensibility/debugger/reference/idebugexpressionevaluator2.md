---
title: IDebugExpressionEvaluator2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b4fc704475c35e9fcd07bba260eb3de9626fe2d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122674"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 代表運算式評估工具 (EE) 的增強型的版本。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 實作這個介面是由運算式評估工具。  
  
## <a name="methods"></a>方法  
 除了上[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|擷取服務物件，指定其唯一的識別項。|  
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|預先載入指定的符號提供者所指定的模組。|  
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|可讓運算式評估工具 (EE)，指定偵錯工具引擎 (DE) 會用來讀取度量設定的回呼介面。|  
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Common language runtime (CLR) 載入偵錯工具中設定的路徑。|  
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|可讓偵錯引擎在初始化期間，傳遞給運算式評估工具的回呼。|  
|[終止](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|停止和清除運算式評估工具。|  
  
## <a name="requirements"></a>需求  
 標頭： Ee.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll