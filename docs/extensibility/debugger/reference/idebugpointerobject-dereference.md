---
title: "IDebugPointerObject::Dereference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerObject::Dereference"
helpviewer_keywords: 
  - "IDebugPointerObject::Dereference 方法"
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得所指向的物件。  
  
## 語法  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### 參數  
 `dwIndex`  
 \[in\]指到的簡單的位元組位移，從物件開始。  
  
 `ppObject`  
 \[\] out傳回[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件代表物件所指向，外加位移，如果有的話。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  如果這個物件不是指向另一個物件，則傳回 E\_FAIL。  
  
## 備註  
 所指向的物件可以是基本型別或複雜的型別，例如類別或結構。  
  
## 請參閱  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)