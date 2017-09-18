---
title: "IDebugProgram2::Terminate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Terminate"
helpviewer_keywords: 
  - "IDebugProgram2::Terminate"
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

結束程式。  
  
## 語法  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```c#  
int Terminate();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 如果可能的話，程式將而終止或從處理序 ； 卸載 否則，偵錯引擎 \(DE\) 會執行任何必要的清除。  
  
 這個方法或[結束](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) IDE 時，通常是在回應停止所有的偵錯的使用者會呼叫方法。  這個方法的實作應該在理想的情況下，終止處理序中的程式。  如果不這麼做，DE 應該防止程式執行更多進行這項工作並進行任何必要的清除。  如果`IDebugProcess2::Terminate`方法受呼叫時 ide、 有時之後，將會終止整個處理序`IDebugProgram2::Terminate` ，會呼叫方法。  
  
## 請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [結束](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)