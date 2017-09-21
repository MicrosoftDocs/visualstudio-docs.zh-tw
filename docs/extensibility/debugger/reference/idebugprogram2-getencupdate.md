---
title: "IDebugProgram2::GetENCUpdate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetENCUpdate"
helpviewer_keywords: 
  - "IDebugProgram2::GetENCUpdate"
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugProgram2::GetENCUpdate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會取得編輯後繼續 \(ENC\) 的更新程式。  自訂的偵錯引擎一定會傳回`E_NOTIMPL`。  
  
## 語法  
  
```cpp#  
HRESULT GetENCUpdate(   
   IUnknown** ppUpdate  
);  
```  
  
```c#  
int GetENCUpdate(  
   out object ppUpdate  
);  
```  
  
#### 參數  
 `ppUpdate`  
 \[\] out傳回內部介面，可用來更新這個程式。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
> [!NOTE]
>  自訂的偵錯引擎應該永遠會傳回`E_NOTIMPL`。  
  
## 請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)