---
title: "IDebugObject2::GetField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::GetField"
helpviewer_keywords: 
  - "IDebugObject2::GetField 方法"
ms.assetid: add6a6b5-e752-47dd-9613-29206ea809b0
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugObject2::GetField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得這個物件的型別。  
  
## 語法  
  
```cpp  
HRESULT GetField(  
 IDebugField** ppField  
);  
```  
  
```c#  
int GetField(  
   out IDebugField ppField  
);  
```  
  
#### 參數  
 `ppField`  
 \[\] out傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，如果沒有 null 值。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 欄位說明的物件型別。  
  
## 請參閱  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)