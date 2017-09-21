---
title: "IDebugReference2::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::GetSize"
helpviewer_keywords: 
  - "IDebugReference2::GetSize"
ms.assetid: a404ddd9-d940-4513-97cd-f52b8ab6a560
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

請取得大小而定，以位元組為單位的參照值。  保留供將來使用。  
  
## 語法  
  
```cpp#  
HRESULT GetSize (   
   DWORD* pdwSize  
);  
```  
  
```c#  
int GetSize (   
   out uint pdwSize  
);  
```  
  
#### 參數  
 `pdwSize`  
 \[\] out會傳回大小而定，以位元組為單位的參照值。  
  
## 傳回值  
 永遠傳回 `E_NOTIMPL`。  
  
## 請參閱  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)