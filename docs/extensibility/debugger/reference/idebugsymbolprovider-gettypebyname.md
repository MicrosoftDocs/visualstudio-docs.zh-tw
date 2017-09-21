---
title: "IDebugSymbolProvider::GetTypeByName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetTypeByName"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetTypeByName 方法"
ms.assetid: b9d88d3b-8b75-484a-b9cc-dc8c0fbb4bc8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetTypeByName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會將符號名稱對應的符號型別。  
  
## 語法  
  
```cpp#  
HRESULT GetTypeByName(   
   LPCOLESTR     pszClassName,  
   NAME_MATCH    nameMatch,  
   IDebugField** ppField  
);  
```  
  
```c#  
int GetTypeByName(  
   string          pszClassName,   
   NAME_MATCH      nameMatch,   
   out IDebugField ppField  
);  
```  
  
#### 參數  
 `pszClassName`  
 \[in\]符號名稱。  
  
 `nameMatch`  
 \[in\]選取的型別符合的項目，例如，區分大小寫。  [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md) 列舉中的值。  
  
 `ppField`  
 \[\] out傳回與符號類型[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法是泛型的版本的[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)。  
  
## 請參閱  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md)   
 [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)