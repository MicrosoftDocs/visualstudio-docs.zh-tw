---
title: "IDebugProgram2::EnumModules | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::EnumModules"
helpviewer_keywords: 
  - "IDebugProgram2::EnumModules"
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::EnumModules
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取一份此程式已載入並且正在執行的模組。  
  
## 語法  
  
```cpp#  
HRESULT EnumModules(   
   IEnumDebugModules2** ppEnum  
);  
```  
  
```c#  
int EnumModules(   
   out IEnumDebugModules2 ppEnum  
);  
```  
  
#### 參數  
 `ppEnum`  
 \[\] out傳回[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)物件，其中包含的模組清單。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 模組是 DLL 或組件，而且通常會列在**模組**偵錯\] 視窗。  
  
## 請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)