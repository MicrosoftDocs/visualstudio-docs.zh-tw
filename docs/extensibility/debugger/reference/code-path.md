---
title: "CODE_PATH | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CODE_PATH"
helpviewer_keywords: 
  - "CODE_PATH 結構"
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# CODE_PATH
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

說明的方法或函式呼叫。  
  
## 語法  
  
```cpp#  
typedef struct tagCODE_PATH {   
   BSTR                bstrName;  
   IDebugCodeContext2* pCode;  
} CODE_PATH;  
```  
  
```c#  
public struct CODE_PATH {  
   public string            bstrName;  
   public IDebugCodeContext pCode;  
}  
```  
  
## Members  
 bstrName  
 程式碼路徑的名稱。  
  
 pCode  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)用來識別程式碼逐步執行函式中的物件。  
  
## 備註  
 這個結構用來實作 \[逐步執行函式。  [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)傳回目前的位置，在偵錯程式中所有的呼叫。  這個結構是表示一個這類的呼叫。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)