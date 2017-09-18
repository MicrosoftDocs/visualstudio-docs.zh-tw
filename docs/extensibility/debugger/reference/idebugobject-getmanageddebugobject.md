---
title: "IDebugObject::GetManagedDebugObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::GetManagedDebugObject"
helpviewer_keywords: 
  - "IDebugObject::GetManagedDebugObject 方法"
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

在偵錯引擎的位址空間中建立一份受管理的物件。  
  
## 語法  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```c#  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### 參數  
 `ppObject`  
 \[\] out傳回[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)物件，代表剛建立的 managed 的物件。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  如果這會傳回 E\_FAIL [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)不能代表受管理的實值類別執行個體。  
  
## 備註  
 這[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件必須表示受管理的實值類別執行個體中，例如`System.Decimal`執行個體。  藉由本機複本，呼叫的額外負荷[評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)就會被淘汰。  
  
## 請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)