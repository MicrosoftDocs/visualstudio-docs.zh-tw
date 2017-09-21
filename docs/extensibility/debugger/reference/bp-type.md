---
title: "BP_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_TYPE"
helpviewer_keywords: 
  - "BP_TYPE 列舉型別"
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定中斷點在程式碼的位置、 資料的位置，還是另一種類型的中斷點。  
  
## 語法  
  
```cpp#  
enum enum_BP_TYPE {   
   BPT_NONE    = 0x0000,  
   BPT_CODE    = 0x0001,  
   BPT_DATA    = 0x0002,  
   BPT_SPECIAL = 0x0003  
};  
typedef DWORD BP_TYPE;  
```  
  
```c#  
public enum enum_BP_TYPE {   
   BPT_NONE    = 0x0000,  
   BPT_CODE    = 0x0001,  
   BPT_DATA    = 0x0002,  
   BPT_SPECIAL = 0x0003  
};  
```  
  
## Members  
 BPT\_NONE  
 不指定任何中斷點類型。  
  
 BPT\_CODE  
 指定程式碼的中斷點。  
  
 BPT\_DATA  
 指定資料中斷點。  
  
 BPT\_SPECIAL  
 指定的程式碼和資料型別都不是中斷點。  這類已被取代，而且不應該使用。  
  
## 備註  
 做為參數來傳遞[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)和[GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)方法。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)