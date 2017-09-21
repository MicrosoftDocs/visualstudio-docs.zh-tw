---
title: "AD_PROCESS_ID_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AD_PROCESS_ID_TYPE"
helpviewer_keywords: 
  - "AD_PROCESS_ID_TYPE 列舉型別"
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定如何解譯在某個處理序識別碼[AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構。  
  
## 語法  
  
```cpp#  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```c#  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## Members  
 AD\_PROCESS\_ID\_SYSTEM  
 處理程序識別碼是系統識別項。  使用`ProcessId.dwProcessId`欄位的[AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構。  
  
 AD\_PROCESS\_ID\_GUID  
 處理序 ID 是 GUID。  使用`ProcessId.guidProcessId`欄位的`AD_PROCESS_ID`結構。  
  
## 備註  
 用於`ProcessIdType`成員的[AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構來識別包含在結構中的處理序 ID 的型別。  決定如何解譯`ProcessId`結構中的聯集。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)