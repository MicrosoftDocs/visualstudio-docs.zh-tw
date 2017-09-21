---
title: "MACHINE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MACHINE_INFO"
helpviewer_keywords: 
  - "MACHINE_INFO 結構"
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# MACHINE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

說明特定的電腦。  
  
## 語法  
  
```cpp#  
typedef struct tagMACHINE_INFO {   
   MACHINE_INFO_FIELDS Fields;  
   BSTR                bstrName;  
   MACHINE_INFO_FLAGS  Flags;  
} MACHINE_INFO;  
```  
  
```c#  
public struct MACHINE_INFO {   
   public uint   Fields;  
   public string bstrName;  
   public uint   Flags;  
};  
```  
  
## Members  
 `Fields`  
 從的旗標組合[MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)指定的結構哪一個欄位都會初始化的列舉型別。  
  
 `bstrName`  
 電腦名稱。  相當於電話[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)。  
  
 `Flags`  
 從的旗標組合[MACHINE\_INFO\_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md)描述機器屬性列舉型別。  
  
## 備註  
 這個結構會傳回由呼叫[GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)方法。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)