---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3f89502beeb1e8165450c7c07f3f55f83dd39e1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
允許 （或不允許），在給定的執行緒上發生，即使程式已停止的運算式評估。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```csharp  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pOriginatingProgram`  
 [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，代表已評估運算式的程式。  
  
 `dwTid`  
 [in]指定執行緒的識別項。  
  
 `dwEvalFlags`  
 [in]從旗標的組合[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)指定評估的執行方式的列舉。  
  
 `pExprCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)用來傳送在運算式評估期間發生的偵錯事件的物件。  
  
 `fWatch`  
 [in]如果不是零 (`TRUE`)，讓運算式評估所識別的執行緒上`dwTid`，否則為零 (`FALSE`) 不允許在該執行緒上的運算式評估。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 工作階段的偵錯管理員 (SDM) 要求時所識別的程式`pOriginatingProgram`參數，以評估運算式，它會呼叫這個方法來通知其他所有附加的程式。  
  
 運算式評估在一個程式中的可能會造成執行位於另一個，因為函式評估或評估的任何程式碼`IDispatch`屬性。 因為這個緣故，這個方法可讓執行並完成即使執行緒可能會停止此程式中的運算式評估。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)