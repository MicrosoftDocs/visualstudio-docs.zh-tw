---
title: "IDebugCoreServer3::GetServerName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::GetServerName"
helpviewer_keywords: 
  - "IDebugCoreServer3::GetServerName"
ms.assetid: 0fc3fcf5-d6a3-4a00-bf14-458b8645714e
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCoreServer3::GetServerName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取伺服器的名稱。  
  
## 語法  
  
```cpp#  
HRESULT GetServerName(  
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetServerName(  
   out string pbstrName  
);  
```  
  
#### 參數  
 `pbstrName`  
 \[\] out傳回伺服器的名稱。  
  
> [!NOTE]
>  呼叫端負責釋出的字串。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 好記的伺服器名稱\] 中，呼叫[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)方法。  
  
## 請參閱  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)