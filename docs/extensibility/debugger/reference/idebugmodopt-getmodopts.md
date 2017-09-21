---
title: "IDebugModOpt::GetModOpts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugModOpt::GetModOpts"
  - "GetModOpts"
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugModOpt::GetModOpts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取一份選擇性修飾詞。  
  
## 語法  
  
```cpp#  
HRESULT GetModOpts(  
   ULONG  celt,  
   BSTR*  rgelt,  
   ULONG* pceltFetched  
);  
```  
  
```c#  
int GetModOpts(  
   uint         celt,  
   out string[] rgelt,  
   ref uint     pceltFetched  
);  
```  
  
#### 參數  
 `celt`  
 \[in\]要傳回的項目數目。  
  
 `rgelt`  
 \[\] out傳回陣列，其中包含的選項。  
  
 `pceltFetched`  
 輸入 \[、 輸出\]在傳回的元素數目`rgelt`陣列。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)