---
title: "IDebugGenericParamField::GetIndex | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugGenericParamField::GetIndex"
ms.assetid: 8e0bdb26-1247-44d9-8d80-ec6e35187fb4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugGenericParamField::GetIndex
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取這個泛用參數的索引。  
  
## 語法  
  
```cpp#  
HRESULT GetIndex(  
   DWORD* pIndex  
);  
```  
  
```c#  
int GetIndex(  
   out uint pIndex  
);  
```  
  
#### 參數  
 `pIndex`  
 \[\] out此泛型參數的索引值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 比方說，如 Dictionary\(K,V\)，k 是索引為 0，v 為索引 1。  
  
## 範例  
 下列範例會示範如何實作這個方法，如 **CDebugGenericParamFieldType** 物件，公開 \(expose\) [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)介面。  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::GetIndex(DWORD* pIndex)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetIndex );  
  
    IfFalseGo(pIndex, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    *pIndex = m_index;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetIndex, hr );  
    return hr;  
}  
```  
  
## 請參閱  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)