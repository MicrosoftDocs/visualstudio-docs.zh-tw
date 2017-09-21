---
title: "IEnumDebugReferenceInfo2::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugReferenceInfo2::Skip"
helpviewer_keywords: 
  - "IEnumDebugReferenceInfo2::Skip"
ms.assetid: 12f07ed8-92bd-47b5-9113-f73fec5bdde6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugReferenceInfo2::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

略過指定的項目數。  
  
## 語法  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```c#  
int Skip(  
   uint celt  
);  
```  
  
#### 參數  
 `celt`  
 \[in\]若要跳過的項目數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果`celt`大於其餘的項目 ； 數目 否則，會傳回錯誤碼。  
  
## 備註  
 如果`celt`指定的值是無效的其餘的項目，列舉型別設定為 \[結束和`S_FALSE`會傳回。  
  
## 請參閱  
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)