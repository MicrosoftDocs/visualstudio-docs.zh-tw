---
title: "IEnumDebugObjects::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugObjects::GetCount"
helpviewer_keywords: 
  - "IEnumDebugObjects::GetCount 方法"
ms.assetid: 9cbc5db4-03ae-479f-a664-13cad66ad210
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IEnumDebugObjects::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會傳回列舉型別中的項目數。  
  
## 語法  
  
```cpp#  
HRESULT GetCount(  
   [out] ULONG* pcelt  
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
 這個方法不會指定只有下一步\]、 複製、 跳過及重設必須實作 COM 習慣性列舉型別介面的一部分。  
  
## 請參閱  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)