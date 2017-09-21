---
title: "IDebugEngine2::SetRegistryRoot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::SetRegistryRoot"
helpviewer_keywords: 
  - "IDebugEngine2::SetRegistryRoot"
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

設定偵錯引擎 \(DE\) 的登錄根目錄。  
  
## 語法  
  
```cpp#  
HRESULT SetRegistryRoot(   
   LPCOLESTR pszRegistryRoot  
);  
```  
  
```c#  
int SetRegistryRoot(   
   string pszRegistryRoot  
);  
```  
  
#### 參數  
 `pszRegistryRoot`  
 \[in\]若要使用的登錄根目錄。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法可讓[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]來指定替代的登錄根目錄 DE 應該用來取得登錄設定。 例如，"HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp"。  
  
## 請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)