---
title: "PROCESS_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROCESS_INFO_FLAGS"
helpviewer_keywords: 
  - "PROCESS_INFO_FLAGS 列舉型別"
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

將告訴您，或指定的處理程序的屬性。  
  
## 語法  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```c#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## Members  
 PIFLAG\_SYSTEM\_PROCESS  
 表示處理程序是一個系統處理序。  
  
 PIFLAG\_DEBUGGER\_ATTACHED  
 指示處理程序正在進行偵錯的偵錯工具。  可能是[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯工具，或者它可能是偵錯一些其他工具，例如 WinDbg。  
  
 PIFLAG\_PROCESS\_STOPPED  
 指示處理程序已停止。  有效的只有當`PIFLAG_DEBUGGER_ATTACHED`指定了。  [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]及更新版本。  
  
 PIFLAG\_PROCESS\_RUNNING  
 指示處理程序正在執行中。  有效的只有當`PIFLAG_DEBUGGER_ATTACHED`指定了。  [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]及更新版本。  
  
## 備註  
 用於`Flags`成員的[PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)結構。  
  
 這些旗標可以使用位元和結合`OR`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)