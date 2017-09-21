---
title: "IEnumDebugProcesses2::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugProcesses2::GetCount"
helpviewer_keywords: 
  - "IEnumDebugProcesses2::GetCount"
ms.assetid: 5dc3e36c-46e5-4556-bf41-1870aa67d2a0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IEnumDebugProcesses2::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

傳回列舉型別中的項目數。  
  
## 語法  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```c#  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### 參數  
 `pcelt`  
 \[\] out傳回列舉型別中的項目數。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法不是自訂的 COM 列舉型別介面，只有指定的`Next`， `Clone`， `Skip`，以及`Reset`必須實作的方法。  
  
## 請參閱  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)