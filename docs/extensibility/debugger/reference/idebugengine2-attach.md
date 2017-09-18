---
title: "IDebugEngine2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::Attach"
helpviewer_keywords: 
  - "IDebugEngine2::Attach"
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugEngine2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

將偵錯引擎 \(DE\) 附加到程式或程式。  工作階段偵錯管理員 \(SDM\) 執行同處理序以 SDM DE 時呼叫。  
  
## 語法  
  
```cpp#  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```c#  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### 參數  
 `pProgram`  
 \[in\]陣列的[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，表示要附加至的程式。  這些都是連接埠的程式。  
  
 `rgpProgramNodes`  
 \[in\]陣列的[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)代表程式的節點，一個用於每個程式的物件。  此陣列中的程式節點代表相同的程式，如`pProgram`。  以便 DE 辨認附加至程式，可以使用 \[程式\] 節點。  
  
 `celtPrograms`  
 \[in\]程式及\/或程式中的節點的數字`pProgram`和`rgpProgramNodes`陣列。  
  
 `pCallback`  
 \[in\][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)是用來將偵錯事件傳送至 SDM 的物件。  
  
 `dwReason`  
 \[in\]介於[ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)指定的原因，讓您附加這些程式的列舉型別。  如需詳細資訊，請參閱＜備註＞一節。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 有三個原因，讓您附加至程式、，如下所示：  
  
-   `ATTACH_REASON_LAUNCH`指出 DE 附加到程式，因為使用者啟動包含它的處理序。  
  
-   `ATTACH_REASON_USER`表示使用者已明確地要求 DE 附加到程式 \(或包含程式的處理序\)。  
  
-   `ATTACH_REASON_AUTO`指出 DE 附加到特定的程式，因為它已經偵錯的其他程式中特定的處理程序。  這也稱為自動附加。  
  
 當呼叫這個方法時，DE 必須依順序傳送這些事件：  
  
1.  [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)\(如果它已經尚未傳送偵錯引擎的特定執行個體\)  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 此外，如果將附加的原因是`ATTACH_REASON_LAUNCH`，DE 需要傳送給[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)事件。  
  
 一次 DE 取得[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件對應到程式的偵錯，它可以查詢任何私用的介面。  
  
 呼叫方法的程式\] 節點中所指定的陣列之前`pProgram`或`rgpProgramNodes`，則模擬，必要時，必須在啟用`IDebugProgram2`介面代表 \[程式\] 節點。  一般情況下，不過，這個步驟並不需要。  如需詳細資訊，請參閱 [安全性問題](../../../extensibility/debugger/security-issues.md)。  
  
## 請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)