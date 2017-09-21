---
title: "IDebugManagedObject::GetManagedObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugManagedObject::GetManagedObject"
helpviewer_keywords: 
  - "IDebugManagedObject::GetManagedObject 方法"
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugManagedObject::GetManagedObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

傳回表示 managed 的物件的介面。  
  
## 語法  
  
```cpp#  
HRESULT GetManagedObject(   
   IUnknown** ppManagedObject  
);  
```  
  
```cpp#  
int GetManagedObject(  
   out object ppManagedObject  
);  
```  
  
#### 參數  
 `ppManagedObject`  
 \[\] out傳回表示 managed 的物件的介面。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法所傳回的介面可以查詢任何 managed 類別，讓它被呼叫的方法實作的介面。  
  
## 請參閱  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)