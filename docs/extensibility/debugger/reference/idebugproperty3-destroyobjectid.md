---
title: "IDebugProperty3::DestroyObjectID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::DestroyObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::DestroyObjectID"
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

終結與此屬性，相關指示呼叫者不會再在乎來識別唯一所有的其他屬性的這個屬性的專一識別碼。  
  
## 語法  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```c#  
int DestroyObjectID();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 如果偵錯引擎不需要支援屬性的唯一識別碼 \(因為它已追蹤它們唯一內部\)，則可以只傳回`E_NOTIMPL`這個方法。  
  
 專一識別碼由呼叫[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)方法，當呼叫端想要確定這個屬性唯一的識別之間所有其他屬性。  
  
## 請參閱  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)