---
title: "DISASSEMBLY_STREAM_SCOPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_STREAM_SCOPE"
helpviewer_keywords: 
  - "DISASSEMBLY_STREAM_SCOPE 列舉型別"
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DISASSEMBLY_STREAM_SCOPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定反組譯碼資料流的範圍。  
  
## 語法  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```c#  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## Members  
 DSS\_HUGE  
 指定反組譯程式碼的內容就會產生比用戶端通常會想要擷取的單一呼叫中的多個輸出。  
  
 DSS\_FUNCTION  
 指定函式所包含的程式碼內容應該反組譯。  指定 \[反組譯碼資料流表示函式時所傳回的[GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md)方法。  
  
 DSS\_MODULE  
 當傳回的`IDebugDisassemblyStream2::GetScope`方法，會指定反組譯碼資料流表示模組。  
  
 DSS\_ALL  
 指定整個位址空間的反組譯碼。  
  
## 備註  
 當做引數傳遞[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)方法，並傳回[GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md)方法。  
  
 這些值可以使用位元和結合`OR`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md)