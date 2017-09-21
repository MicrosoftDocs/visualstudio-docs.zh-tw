---
title: "IDebugObject::IsReadOnly | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::IsReadOnly"
helpviewer_keywords: 
  - "IDebugObject::IsReadOnly 方法"
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::IsReadOnly
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

判斷這個物件是否為唯讀。  
  
## 語法  
  
```cpp#  
HRESULT IsReadOnly(   
   BOOL* pfIsReadOnly  
);  
```  
  
```c#  
int IsReadOnly(  
   out int pfIsReadOnly  
);  
```  
  
#### 參數  
 `pfIsReadOnly`  
 \[\] out傳回非零 \(`TRUE`\) 如果這個物件是唯讀的。 否則，會傳回零 \(`FALSE`\)。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 唯讀屬性的物件不能建立後變更其值。  
  
## 請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)