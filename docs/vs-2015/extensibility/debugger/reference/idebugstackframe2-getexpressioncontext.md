---
title: IDebugStackFrame2::GetExpressionContext |Microsoft Docs
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
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: be81a74f9ce13511e463c4244fc1e817f5c94d1d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940628"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得目前的內容中的運算式評估的堆疊框架和執行緒評估內容。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```csharp  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppExprCxt`  
 [out]傳回[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)物件，表示運算式評估的內容。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 一般而言，運算式評估內容可以視為執行運算式評估的範圍。 呼叫[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法來剖析的運算式，然後呼叫 產生[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或是[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)方法，以評估剖析的運算式。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)

