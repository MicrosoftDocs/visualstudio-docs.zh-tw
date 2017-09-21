---
title: "IDebugAlias::Dispose | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias::Dispose"
helpviewer_keywords: 
  - "IDebugAlias::Dispose 方法"
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugAlias::Dispose
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

標示為移除這個別名。  
  
## 語法  
  
```cpp  
HRESULT Dispose();  
```  
  
```c#  
int Dispose();  
```  
  
#### 參數  
 無。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 一旦呼叫這個方法時，已無法使用別名。  
  
## 請參閱  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)