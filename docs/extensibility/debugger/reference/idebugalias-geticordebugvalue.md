---
title: "IDebugAlias::GetICorDebugValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias::GetICorDebugValue"
helpviewer_keywords: 
  - "IDebugAlias::GetICorDebugValue 方法"
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取的 managed 程式碼介面，表示此別名相關聯的值。  
  
## 語法  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### 參數  
 `ppUnk`  
 \[out\] `IUnknown` 介面，代表與此別名相關聯的值。 您可以查詢此介面 `ICorDebugValue` 介面。  
  
## 傳回值  
 如果成功，會傳回 S\_OK。否則，傳回錯誤碼。  
  
## 備註  
 這個方法只適用於受管理的值 \( `ICorDebugValue` 在可用介面 [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] 並定義於 [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK cordebug.idl 檔案中的\)。  
  
## 請參閱  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)