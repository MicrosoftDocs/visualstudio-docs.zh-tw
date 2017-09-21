---
title: "IDebugCustomAttributeQuery2::EnumCustomAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttributeQuery2::EnumCustomAttributes"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery2::EnumCustomAttributes"
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCustomAttributeQuery2::EnumCustomAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得附加至這個欄位的所有自訂屬性的列舉值。  
  
## 語法  
  
```cpp#  
HRESULT EnumCustomAttributes(   
   IEnumDebugCustomAttributes** ppEnum  
);  
```  
  
```c#  
int EnumCustomAttributes(  
   out IEnumDebugCustomAttributes ppEnum  
);  
```  
  
#### 參數  
 `ppEnum`  
 \[\] out傳回[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)物件，表示清單中的自訂屬性。 如果沒有自訂屬性，否則傳回 null 值。  
  
## 傳回值  
 如果成功的話，傳回 S\_OK 或 S\_FALSE，如果這個欄位中沒有自訂屬性。  否則，會傳回錯誤碼 ；  
  
## 備註  
 欄位可以擁有多個自訂屬性。  
  
## 請參閱  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)