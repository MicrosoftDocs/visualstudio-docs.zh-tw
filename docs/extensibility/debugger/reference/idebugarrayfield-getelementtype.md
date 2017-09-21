---
title: "IDebugArrayField::GetElementType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayField::GetElementType"
helpviewer_keywords: 
  - "IDebugArrayField::GetElementType 方法"
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayField::GetElementType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得陣列中的項目的型別。  
  
## 語法  
  
```cpp#  
HRESULT GetElementType(   
   IDebugField** ppType  
);  
```  
  
```c#  
int GetElementType(  
   out IDebugField ppType  
);  
```  
  
#### 參數  
 `ppType`  
 \[\] out傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，描述項目的型別。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)物件會假設所有陣列元素都都是相同的型別。  
  
## 請參閱  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)