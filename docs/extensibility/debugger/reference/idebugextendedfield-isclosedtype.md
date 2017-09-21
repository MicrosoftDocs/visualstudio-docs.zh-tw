---
title: "IDebugExtendedField::IsClosedType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IsClosedType"
  - "IDebugExtendedField::IsClosedType"
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExtendedField::IsClosedType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

決定是否欄位會表示封閉型別。  
  
## 語法  
  
```cpp#  
HRESULT IsClosedType(  
   void  
);  
```  
  
```c#  
int IsClosedType();  
```  
  
## 傳回值  
 如果欄位是封閉式的型別，會傳回`S_OK`。 否則，會傳回`S_FALSE`。  
  
## 請參閱  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)