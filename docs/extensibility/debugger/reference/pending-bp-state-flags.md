---
title: "PENDING_BP_STATE_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PENDING_BP_STATE_FLAGS"
helpviewer_keywords: 
  - "PENDING_BP_STATE_FLAGS 列舉型別"
ms.assetid: 85522449-3fd8-4da5-b0fe-a43160e0c33b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# PENDING_BP_STATE_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定的暫止中斷點狀態旗標。  
  
## 語法  
  
```cpp#  
enum enum_PENDING_BP_STATE_FLAGS {   
   PBPSF_NONE        = 0x0000,  
   PBPSF_VIRTUALIZED = 0x0001  
};  
typedef DWORD PENDING_BP_STATE_FLAGS;  
```  
  
```c#  
public enum enum_PENDING_BP_STATE_FLAGS {   
   PBPSF_NONE        = 0x0000,  
   PBPSF_VIRTUALIZED = 0x0001  
};  
```  
  
## Members  
 PBPSF\_NONE  
 版面配置區。  
  
 PBPSF\_VIRTUALIZED  
 指定虛擬化暫止中斷點，另一個則是每次載入新的程式碼，繫結。  
  
## 備註  
 用於`flags`成員的[PENDING\_BP\_STATE\_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)結構。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING\_BP\_STATE\_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)