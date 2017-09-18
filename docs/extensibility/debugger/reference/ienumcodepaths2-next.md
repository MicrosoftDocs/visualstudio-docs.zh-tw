---
title: "IEnumCodePaths2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCodePaths2::Next"
helpviewer_keywords: 
  - "IEnumCodePaths2::Next"
ms.assetid: c7a8fe97-2abc-4cee-8aef-64f1daa93b5c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IEnumCodePaths2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

傳回下一個項目從集合的列舉型別。  
  
## 語法  
  
```cpp#  
HRESULT Next(  
   ULONG       celt,  
   CODE_PATH** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint        celt,  
   CODE_PATH[] rgelt,  
   ref uint    pceltFetched  
);  
```  
  
#### 參數  
 `celt`  
 \[in\]若要擷取的項目數。  也會指定最大`rgelt`陣列。  
  
 `rgelt`  
 輸入 \[、 輸出\]陣列的[CODE\_PATH](../../../extensibility/debugger/reference/code-path.md)會自動填入的項目。  
  
 `pceltFetched`  
 \[\] out傳回以實際傳回的項目數`rgelt`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果少於無法傳回所要求的項目數目。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md)