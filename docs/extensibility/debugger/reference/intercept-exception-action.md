---
title: "INTERCEPT_EXCEPTION_ACTION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "INTERCEPT_EXCEPTION_ACTION"
helpviewer_keywords: 
  - "INTERCEPT_EXCEPTION_ACTION 列舉型別"
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# INTERCEPT_EXCEPTION_ACTION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定當攔截例外狀況時要採取什麼動作。  
  
## 語法  
  
```cpp#  
enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
typedef DWORD INTERCEPT_EXCEPTION_ACTION;  
```  
  
```c#  
public enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
```  
  
#### 參數  
 IEA\_INTERCEPT  
 可以攔截目前例外狀況。  這是唯一支援目前的值，而且必須指定。  
  
## 備註  
 這些值會傳遞至[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)方法。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)