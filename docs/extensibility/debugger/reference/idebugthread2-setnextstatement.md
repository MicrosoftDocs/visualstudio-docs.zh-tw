---
title: IDebugThread2::SetNextStatement |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e59d4087e44458ecd49efd5d7be9f45e68c6da2b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
將目前指令指標設定為指定的程式碼內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pStackFrame`  
 保留供未來使用。設定為 null 的值。  
  
 `pCodeContext`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)描述將要執行的程式碼位置的物件和其內容。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 下表顯示其他可能的值。  
  
|值|描述|  
|-----------|-----------------|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|下一個陳述式不能在更深入的堆疊框架上的堆疊框架。|  
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|下一個陳述式不是堆疊中的任何框架相關聯。|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|有些偵錯引擎無法設定例外狀況之後的下一個陳述式。|  
  
## <a name="remarks"></a>備註  
 指令指標表示下一個指令或陳述式來執行。 這個方法用來重試一次一行程式碼或強制執行，例如在另一個函式，繼續執行。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)