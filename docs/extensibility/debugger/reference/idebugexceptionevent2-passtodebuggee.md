---
title: "IDebugExceptionEvent2::PassToDebuggee |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords: IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4abb59c9bf9717089353683087c38425d3bf88ed
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
指定例外狀況應該傳遞給程式進行偵錯時就會繼續執行，或如果應該捨棄例外狀況。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fPass`  
 [in]非零 (`TRUE`) 如果例外狀況應該傳遞給程式進行偵錯時就會繼續執行，則為零 (`FALSE`) 如果應該捨棄例外狀況。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 呼叫這個方法並不會實際會在偵錯程式中執行的任何程式碼。 呼叫只是要設定下一個程式碼執行狀態。 例如，若要呼叫[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)方法可能會傳回`S_OK`與[EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)。`dwState` 欄位設定為`EXCEPTION_STOP_SECOND_CHANCE`。  
  
 IDE，可能會收到[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)事件和呼叫[繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)方法。 偵錯引擎 (DE) 應該會有預設的行為來處理則`PassToDebuggee`不會呼叫方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)