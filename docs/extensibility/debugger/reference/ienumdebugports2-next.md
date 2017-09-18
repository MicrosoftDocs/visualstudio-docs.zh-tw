---
title: "IEnumDebugPorts2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPorts2::Next"
helpviewer_keywords: 
  - "IEnumDebugPorts2::Next"
ms.assetid: 3f43d18c-6bd1-4ddd-95ef-9550abd2ad09
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugPorts2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

傳回下一個項目從集合的列舉型別。  
  
## 語法  
  
```cpp#  
HRESULT Next(  
   ULONG         celt,  
   IDebugPort2** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint          celt,  
   IDebugPort2[] rgelt,  
   ref uint      pceltFetched  
);  
```  
  
#### 參數  
 `celt`  
 \[in\]若要擷取的項目數。  也會指定最大`rgelt`陣列。  
  
 `rgelt`  
 輸入 \[、 輸出\]陣列的[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)會自動填入的項目。  
  
 `pceltFetched`  
 \[\] out傳回以實際傳回的項目數`rgelt`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果少於無法傳回所要求的項目數目。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)