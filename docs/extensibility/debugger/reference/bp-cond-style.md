---
title: "BP_COND_STYLE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_COND_STYLE"
helpviewer_keywords: 
  - "BP_COND_STYLE 列舉型別"
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定的暫止中斷點條件樣式，並繫結中斷點。  
  
## 語法  
  
```cpp#  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```c#  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## Members  
 BP\_COND\_NONE  
 當到達中斷點位置時，就會引發中斷點。  沒有指定中斷點條件。  
  
 BP\_COND\_WHEN\_TRUE  
 只有當條件式運算式聯中斷點會評估為，將中斷點就會引發`true`。  
  
 BP\_COND\_WHEN\_CHANGED  
 只有在條件式運算式的值相關聯的中斷點時中斷點已經從先前的評估引發。  
  
## 備註  
 用於`styleCondition`成員的[BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)結構。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)