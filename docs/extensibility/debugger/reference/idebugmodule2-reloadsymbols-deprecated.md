---
title: "IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2::ReloadSymbols"
helpviewer_keywords: 
  - "IDebugModule2::ReloadSymbols 方法"
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

已過時。  請勿使用。  重新載入這個模組的符號。  
  
## 語法  
  
```cpp#  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```c#  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### 參數  
 `pszUrlToSymbols`  
 \[in\]符號存放區的路徑。  
  
 `pbstrDebugMessage`  
 \[\] out傳回資訊的訊息，例如狀態或錯誤訊息，顯示右邊的 \[模組\] 視窗中的模組名稱。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  偵錯引擎應該永遠會傳回`E_FAIL`。  
  
## 備註  
 這個方法已不再受支援。  實作[LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md)方法相反。  
  
## 請參閱  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md)