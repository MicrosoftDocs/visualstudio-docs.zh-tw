---
title: IDebugExpressionContext2 |Microsoft Docs
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
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c6cfa4daf038eef4d96f71ab650b621afad5c07
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739018"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面代表運算式評估的內容  
  
## <a name="syntax"></a>語法  
  
```  
IDebugExpressionContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎 (DE) 會實作這個介面來表示可以在其中評估運算式的內容。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)傳回這個介面。 只有在已暫停，正在偵錯程式，而一個堆疊框架是可存取此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugExpressionContext2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|擷取評估內容的名稱。|  
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|剖析的文字為基礎的運算式進行評估。|  
  
## <a name="remarks"></a>備註  
 評估內容可以視為執行運算式評估的範圍。  
  
 當程式已停止執行時，工作階段的偵錯管理員 (SDM) 會從呼叫 DE 取得堆疊框架[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)。 然後呼叫 SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)若要取得`IDebugExpressionContext2`介面。 這之後藉由呼叫[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)來建立[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)介面，表示剖析準備要評估的運算式。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)

