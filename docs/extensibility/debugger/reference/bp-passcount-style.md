---
title: "BP_PASSCOUNT_STYLE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_PASSCOUNT_STYLE"
helpviewer_keywords: 
  - "BP_PASSCOUNT_STYLE 結構"
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_PASSCOUNT_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定的條件會造成該中斷點觸發中斷點傳遞次數相關聯。  
  
## 語法  
  
```cpp#  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```c#  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## Members  
 BP\_PASSCOUNT\_NONE  
 指定無中斷點行程計數樣式。  
  
 BP\_PASSCOUNT\_EQUAL  
 設定為相同的中斷點行程計數樣式。  中斷點叫用次數等於次計數時，中斷點就會引發。  
  
 BP\_PASSCOUNT\_EQUAL\_OR\_GREATER  
 將中斷點行程計數樣式設定為相等或更大。  中斷點叫用次數等於或大於次計數時，中斷點就會引發。  
  
 BP\_PASSCOUNT\_MOD  
 指定模數通過計數。  例如，如果傳遞的計數為型別的`BP_PASSCOUNT_MOD`而階段的 \[計數\] 值為 4，中斷點引發，每次叫用的次數是 4 的倍數。  
  
## 備註  
 用於`stylePassCount`成員的[BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)又是成員的結構[BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)和[BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)