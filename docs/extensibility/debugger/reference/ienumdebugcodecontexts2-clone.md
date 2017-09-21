---
title: "IEnumDebugCodeContexts2::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugCodeContexts2::Clone"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2::Clone"
ms.assetid: 22c98975-4294-4fbd-a345-16f65fe1200d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugCodeContexts2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

傳回一份目前的列舉型別為個別物件。  
  
## 語法  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugCodeContexts2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugCodeContexts2 ppEnum  
);  
```  
  
#### 參數  
 `ppEnum`  
 \[\] out傳回這個列舉型別，為個別物件的複本。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 列舉型別的複製，會呼叫這個方法只有在有與原始檔案相同的狀態。  不過，副本和原本的狀態是分開，且可以個別變更。  
  
## 請參閱  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)