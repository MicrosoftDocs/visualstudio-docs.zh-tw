---
title: "IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::WatchForThreadStep"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForThreadStep"
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugEngineProgram2::WatchForThreadStep
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

監看執行 \(或停止監控執行\) 發生於指定的執行緒。  
  
## 語法  
  
```cpp#  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```c#  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### 參數  
 `pOriginatingProgram`  
 \[in\][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，表示程式正螞蟻。  
  
 `dwTid`  
 \[in\]指定要監看執行緒的識別項。  
  
 `fWatch`  
 \[in\]非零值 \(`TRUE`\) 的方式開始觀賞所識別的執行緒上執行`dwTid`。 否則，零 \(`FALSE`\) 的方式停止在監看執行`dwTid`。  
  
 `dwFrame`  
 \[in\]指定控制步驟類型框架索引。  當這值是零 \(0\)、 步驟類型是 「 進入 」 以及所識別的執行緒時，應該停止程式`dwTid`會執行。  當`dwFrame`為非零，步驟類型是 「 逐程序 」，而且程式會停止所識別的執行緒時，才`dwTid`正在執行中框架，其索引為等於或超過堆疊中較`dwFrame`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 當工作階段偵錯管理員 \(SDM\) 逐步執行程式，由`pOriginatingProgram`參數，它告知所有其他附加的程式呼叫這個方法。  
  
 這個方法是只適用於逐步執行同一個執行緒。  
  
## 請參閱  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)