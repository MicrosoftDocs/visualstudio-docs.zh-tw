---
title: "CONTEXT_COMPARE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CONTEXT_COMPARE"
helpviewer_keywords: 
  - "CONTEXT_COMPARE 列舉型別"
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# CONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定的準則，來比較兩個記憶體內容。  
  
## 語法  
  
```cpp#  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```c#  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## Members  
 CONTEXT\_EQUAL  
 相當於目標的記憶體內容的清單中找到的第一個記憶體內容。  
  
 CONTEXT\_LESS\_THAN  
 小於目標的記憶體內容的清單中找到的第一個記憶體內容。  
  
 CONTEXT\_GREATER\_THAN  
 大於目標的記憶體內容的清單中找到的第一個記憶體內容。  
  
 CONTEXT\_LESS\_THAN\_OR\_EQUAL  
 在第一個記憶體內容中找到小於或等於目標的記憶體內容的清單。  
  
 CONTEXT\_GREATER\_THAN\_OR\_EQUAL  
 大於或等於目標的記憶體內容的清單中找到的第一個記憶體內容。  
  
 CONTEXT\_SAME\_SCOPE  
 在相同的範圍做為目標的記憶體內容的清單中找到的第一個記憶體內容。  
  
 CONTEXT\_SAME\_FUNCTION  
 在清單中位於相同的函式，為目標的記憶體範圍中找到的第一個記憶體內容。  
  
 CONTEXT\_SAME\_MODULE  
 在相同的模組，做為目標的記憶體內容的清單中找到的第一個記憶體內容。  
  
 CONTEXT\_SAME\_PROCESS  
 位於相同的程序，做為目標的記憶體內容的清單中找到的第一個記憶體內容。  
  
## 備註  
 當做引數傳遞[比較](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)方法。  
  
 這些值用來尋找符合指定的比較準則清單中的第一個記憶體內容。  記憶體內容有一份記憶體內容相本身針對透過`IDebugMemoryContext2::Compare`方法。  在清單中是比較運算子的第一個記憶體內容`true`接下來會傳回。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [比較](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)