---
title: "IPropertyProxyEESide::CreateReplacementObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::CreateReplacementObject"
helpviewer_keywords: 
  - "IPropertyProxyEESide::CreateReplacementObject"
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立一份資料物件的特定運算式評估工具 \(EE\)。  
  
## 語法  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### 參數  
 `dataIn`  
 \[in\][IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)持有的資料来複製的物件。  
  
 `dataOut`  
 \[\] out傳回新的`IEEDataStorage`物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法會提供[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件，表示的位元組陣列。  這個連入的資料物件通常不會實作得知 ee 給予。  不過，這個方法所傳回的物件一律實作得知 ee 給予，它可讓 EE 實作`IEEDataStorage`上想要的任何類別的介面。  
  
 請注意資料提供連入的`IEEDataStorage`物件必須是相同的資料中的連出`IEEDataStorage`物件。  
  
## 請參閱  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)