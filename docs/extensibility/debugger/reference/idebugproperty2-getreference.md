---
title: "IDebugProperty2::GetReference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetReference"
helpviewer_keywords: 
  - "IDebugProperty2::GetReference 方法"
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::GetReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

傳回屬性值的參考。  
  
## 語法  
  
```cpp#  
HRESULT GetReference(  
   IDebugReference2** ppReference  
);  
```  
  
```c#  
int GetReference(  
   out IDebugReference2 ppReference  
);  
```  
  
#### 參數  
 `ppRererence`  
 \[\] out傳回[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件，表示屬性值的參考。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼，通常是`E_NOTIMPL`或`E_GETREFERENCE_NO_REFERENCE`。  
  
## 請參閱  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)