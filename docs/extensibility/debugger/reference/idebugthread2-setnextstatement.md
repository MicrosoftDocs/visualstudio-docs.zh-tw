---
title: "IDebugThread2::SetNextStatement |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::SetNextStatement
helpviewer_keywords: IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6dd345fe298af42a69ac076bf92de7df9db82ec2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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
  
|值|說明|  
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