---
title: "IPropertyProxyEESide::GetInitialData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::GetInitialData"
helpviewer_keywords: 
  - "IPropertyProxyEESide::GetInitialData"
ms.assetid: 36cceb19-2604-4ef9-b42b-5dd30cbe24b1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyEESide::GetInitialData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

傳回此物件的初始資料。  
  
## 語法  
  
```cpp#  
HRESULT GetInitialData(  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int GetInitialData(  
   out IEEDataStorage dataOut  
);  
```  
  
#### 參數  
 `dataOut`  
 \[\] out傳回[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件，包含這個物件的初始資料。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)