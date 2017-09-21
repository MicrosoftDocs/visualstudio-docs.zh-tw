---
title: "IDebugBinder3::GetAllAliases | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetAllAliases"
helpviewer_keywords: 
  - "IDebugBinder3::GetAllAliases 方法"
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugBinder3::GetAllAliases
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會擷取與該程式的別名清單。  
  
## 語法  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```c#  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### 參數  
 `uRequest`  
 \[in\]要傳回的別名的最大數目 \(指定長度的陣列傳遞至`ppAliases`\)。  
  
 `ppAliases`  
 輸入 \[、 輸出\]要填入陣列中的別名 \(如果是 null 值和`uRequest`為 0，別名可以傳回的計數將會傳回由`puFetched`\)。  
  
 `puFetched`  
 \[\] out傳回取得的別名數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)