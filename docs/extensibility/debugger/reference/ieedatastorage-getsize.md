---
title: "IEEDataStorage::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEDataStorage::GetSize"
helpviewer_keywords: 
  - "IEEDataStorage::GetSize"
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEEDataStorage::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

傳回這個物件中所含的位元組數目。  
  
## 語法  
  
```cpp#  
HRESULT GetSize(  
   ULONG* size  
);  
```  
  
```c#  
int GetSize(  
   out uint size  
);  
```  
  
#### 參數  
 `size`  
 \[\] out這個物件中所含的位元組數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 使用[GetData](../Topic/IEEDataStorage::GetData.md)方法來擷取實際的資料位元組。  
  
## 請參閱  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetData](../Topic/IEEDataStorage::GetData.md)