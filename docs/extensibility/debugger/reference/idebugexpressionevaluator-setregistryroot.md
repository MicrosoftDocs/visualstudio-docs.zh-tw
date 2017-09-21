---
title: "IDebugExpressionEvaluator::SetRegistryRoot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::SetRegistryRoot"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::SetRegistryRoot 方法"
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會設定登錄根目錄。  使用並排顯示偵錯。  
  
## 語法  
  
```cpp#  
HRESULT SetRegistryRoot (   
   LPCOLESTR ustrRegistryRoot  
);  
```  
  
```c#  
int SetRegistryRoot(  
   string ustrRegistryRoot  
);  
```  
  
#### 參數  
 `ustrRegistryRoot`  
 \[in\]新的登錄根目錄。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 當運算式評估工具會先執行個體化，並指出指定的登錄根目錄通常設定為 Visual Studio 的特定版本的登錄機碼 \(HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*X.Y*，其中  *X.Y* 是版本號碼\)。  
  
## 請參閱  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)