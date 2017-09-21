---
title: "IDebugThread2::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::SetNextStatement"
helpviewer_keywords: 
  - "IDebugThread2::SetNextStatement"
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::SetNextStatement
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

將目前的指令指標設定至指定的程式碼的內容。  
  
## 語法  
  
```cpp#  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```c#  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### 參數  
 `pStackFrame`  
 保留供日後使用。 設定為 null 值。  
  
 `pCodeContext`  
 \[in\][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)告訴您，將要執行的程式碼位置的物件和其內容。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  下表顯示其他可能的值。  
  
|值|描述|  
|-------|--------|  
|E\_CANNOT\_SET\_NEXT\_STATEMENT\_ON\_NONLEAF\_FRAME|下一個陳述式不能是框架堆疊上更深入的堆疊框架中。|  
|E\_CANNOT\_SETIP\_TO\_DIFFERENT\_FUNCTION|下一個陳述式不在堆疊中的任何框架相關聯。|  
|E\_CANNOT\_SET\_NEXT\_STATEMENT\_ON\_EXCEPTION|有些偵錯引擎無法設定例外狀況之後的下一個陳述式。|  
  
## 備註  
 指令指標表示下一個指令或陳述式來執行。  若要再試一次一系列的原始程式碼或強制執行，以繼續執行另一個函式，例如，將使用這個方法。  
  
## 請參閱  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)