---
title: "IDebugArrayField::GetRank | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayField::GetRank"
helpviewer_keywords: 
  - "IDebugArrayField::GetRank 方法"
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得的順位或陣列的維度數目。  
  
## 語法  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```c#  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### 參數  
 `pdwRank`  
 \[\] out傳回陣序規範。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 陣列的陣序規範會對應到維度的數目。  在 c \+ \+ 和 C\#，多維陣列其實是陣列的陣列，因此可以視為只是一維陣列 \(和`GetRank`方法一定會傳回 1\)。  在[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]，相反地，多維陣列會以不同方式處理，而且這類陣列的陣序規範的反應的維度數目 \(和`GetRank`方法一定會傳回的維度數目\)。  
  
## 請參閱  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)