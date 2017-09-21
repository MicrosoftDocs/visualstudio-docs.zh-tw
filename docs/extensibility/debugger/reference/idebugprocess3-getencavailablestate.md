---
title: "IDebugProcess3::GetENCAvailableState | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::GetENCAvailableState"
helpviewer_keywords: 
  - "IDebugProcess3::GetENCAvailableState"
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProcess3::GetENCAvailableState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會取得目前的編輯後繼續\] 狀態的處理程序。  自訂的連接埠提供者應該永遠會傳回`E_NOTIMPL`。  
  
## 語法  
  
```cpp  
HRESULT GetENCAvailableState(  
   EncUnavailableReason* pReason  
);  
```  
  
```c#  
int GetENCAvailableState(  
   EncUnavailableReason[] pReason  
);  
```  
  
#### 參數  
 `pReason`  
 \[\] out介於[EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)列舉型別。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
> [!NOTE]
>  自訂的連接埠提供者應該永遠會傳回`E_NOTIMPL`。  
  
## 備註  
 此狀態下會受到[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)。  
  
## 請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)