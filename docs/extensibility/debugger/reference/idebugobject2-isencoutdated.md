---
title: "IDebugObject2::IsEncOutdated | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::IsEncOutdated"
helpviewer_keywords: 
  - "IDebugObject2::IsEncOutdated 方法"
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugObject2::IsEncOutdated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會判斷這個物件或父容器的編輯後繼續狀態是否已過期。  自訂運算式評估工具不會實作這個方法，並永遠傳回`E_NOTIMPL`。  
  
## 語法  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```c#  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### 參數  
 `pfEncOutdated`  
 \[\] out非零值 \(`TRUE`\) 如果編輯後繼續狀態已過期，卻只有 0 \(`FALSE`\) 如果它不是。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
> [!NOTE]
>  自訂運算式評估工具應該永遠會傳回`E_NOTIMPL`。  
  
## 請參閱  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)