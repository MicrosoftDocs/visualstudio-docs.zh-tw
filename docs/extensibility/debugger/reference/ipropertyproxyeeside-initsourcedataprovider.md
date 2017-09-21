---
title: "IPropertyProxyEESide::InitSourceDataProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::InitSourceDataProvider"
helpviewer_keywords: 
  - "IPropertyProxyEESide::InitSourceDataProvider"
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyEESide::InitSourceDataProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

初始化這個物件的來源資料並傳回物件，其中包含初始資料。  
  
## 語法  
  
```cpp#  
HRESULT InitSourceDataProvider(  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int InitSourceDataProvider(  
   out IEEDataStorage dataOut  
);  
```  
  
#### 參數  
 `dataOut`  
 \[\] out傳回[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法沒有項目，即需要初始化的物件，因此它可以傳回[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)介面上物件的資料。  這可讓物件的資料，以檢視並，如果允許的話，由型別視覺化檢視的變更。  
  
## 請參閱  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)