---
title: "IDebugCustomAttribute::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttribute::GetName"
helpviewer_keywords: 
  - "IDebugCustomAttribute::GetName"
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCustomAttribute::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得自訂屬性的名稱。  
  
## 語法  
  
```cpp#  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```c#  
int GetName(  
   out string bstrName  
);  
```  
  
#### 參數  
 `bstrName`  
 \[\] out傳回字串，包含自訂屬性的名稱。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法傳回具名會對應到用來宣告屬性類別的名稱。  這可能不完全對應到自訂屬性類別本身的名稱 C\# 可讓"屬性"後置字元，在宣告中使用時要卸除與自訂屬性名稱。  
  
## 請參閱  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)