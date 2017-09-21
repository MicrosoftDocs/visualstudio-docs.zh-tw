---
title: "REFERENCE_COMPARE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "REFERENCE_COMPARE"
helpviewer_keywords: 
  - "REFERENCE_COMPARE 列舉型別"
ms.assetid: e31cdc78-f621-498b-9ca4-aefa790b9f6f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# REFERENCE_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定參考的比較類型。  
  
## 語法  
  
```cpp#  
enum enum_REFERENCE_COMPARE {   
   REF_COMPARE_EQUAL        = 0x0001,  
   REF_COMPARE_LESS_THAN    = 0x0002,  
   REF_COMPARE_GREATER_THAN = 0x0003  
};  
typedef DWORD REFERENCE_COMPARE;  
```  
  
```c#  
public enum enum_REFERENCE_COMPARE {   
   REF_COMPARE_EQUAL        = 0x0001,  
   REF_COMPARE_LESS_THAN    = 0x0002,  
   REF_COMPARE_GREATER_THAN = 0x0003  
};  
```  
  
## Members  
 REF\_COMPARE\_EQUAL  
 指定等於的比較。  
  
 REF\_COMPARE\_LESS\_THAN  
 指定小於\-比比較。  
  
 REF\_COMPARE\_GREATER\_THAN  
 指定大於\-比比較。  
  
## 備註  
 當做引數傳遞[比較](../../../extensibility/debugger/reference/idebugreference2-compare.md)方法。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [比較](../../../extensibility/debugger/reference/idebugreference2-compare.md)