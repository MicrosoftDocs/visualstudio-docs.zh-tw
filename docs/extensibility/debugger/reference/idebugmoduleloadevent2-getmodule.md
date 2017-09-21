---
title: "IDebugModuleLoadEvent2::GetModule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModuleLoadEvent2::GetModule"
helpviewer_keywords: 
  - "IDebugModuleLoadEvent2::GetModule"
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugModuleLoadEvent2::GetModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得模組正在載入或卸載。  
  
## 語法  
  
```cpp#  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```c#  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### 參數  
 `pModule`  
 \[\] out傳回[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)物件，代表載入或卸載的模組。  
  
 `pbstrDebugMessage`  
 輸入 \[、 輸出\]傳回選擇性的訊息，說明這個事件。  如果這個參數為 null 值，會不要求任何訊息。  
  
 `pbLoad`  
 輸入 \[、 輸出\]非零值 \(`TRUE`\) 如果模組是載入和零 \(`FALSE`\) 如果您正在卸載模組。  如果這個參數為 null 值，會不要求任何狀態。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)