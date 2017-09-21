---
title: "IDebugExpressionEvaluator2::SetIDebugIDECallback | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator2::SetIDebugIDECallback"
  - "SetIDebugIDECallback"
ms.assetid: f01c40ad-ef4b-477b-8304-602c6972bc88
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionEvaluator2::SetIDebugIDECallback
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

啟用偵錯引擎初始化期間，回呼傳遞給運算式評估工具。  
  
## 語法  
  
```cpp#  
HRESULT SetIDebugIDECallback (  
   IDebugIDECallback * pCallback  
);  
```  
  
```c#  
int SetIDebugIDECallback (  
   IDebugIDECallback pCallback  
);  
```  
  
#### 參數  
 `pCallback`  
 \[in\]回呼介面。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)