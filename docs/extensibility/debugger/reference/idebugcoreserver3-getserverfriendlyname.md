---
title: "IDebugCoreServer3::GetServerFriendlyName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::GetServerFriendlyName"
helpviewer_keywords: 
  - "IDebugCoreServer3::GetServerFriendlyName"
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCoreServer3::GetServerFriendlyName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取伺服器的易記名稱。  
  
## 語法  
  
```cpp#  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### 參數  
 `pbstrName`  
 \[\] out傳回伺服器的易記名稱。  
  
> [!NOTE]
>  呼叫端負責釋出的字串。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 使用者啟動的伺服器，這個方法所傳回的名稱會是伺服器的完整名稱。  若為自動啟動伺服器，名稱會是電腦的伺服器上執行。  
  
 機器導向的名稱，呼叫[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)方法。  
  
## 請參閱  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)