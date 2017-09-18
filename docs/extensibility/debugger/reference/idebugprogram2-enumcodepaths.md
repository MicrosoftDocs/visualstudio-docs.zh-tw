---
title: "IDebugProgram2::EnumCodePaths | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::EnumCodePaths"
helpviewer_keywords: 
  - "IDebugProgram2::EnumCodePaths"
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取一份原始程式檔中指定位置的程式碼路徑。  
  
## 語法  
  
```cpp#  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```c#  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### 參數  
 `pszHint`  
 \[in\]在游標下的 word **來源** 或 **反組譯碼**在 IDE 中的檢視。  
  
 `pStart`  
 \[in\][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件，代表目前的程式碼內容。  
  
 `pFrame`  
 \[in\][IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)與目前的中斷點表示的堆疊框架相關聯的物件。  
  
 `fSource`  
 \[in\]非零值 \(`TRUE`\) 如果在**來源** 檢視中，則為零 \(`FALSE`\) 如果在**反組譯碼**檢視。  
  
 `ppEnum`  
 \[\] out傳回[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)物件，其中包含程式碼路徑的清單。  
  
 `ppSafety`  
 \[\] out傳回[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件代表設定為中斷點，如果選擇的程式碼路徑不額外的程式碼的內容就會遭到省略。  這可能會發生的最少運算的布林運算式，例如。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 程式碼路徑則描述方法或函式所呼叫以取得目前程式的執行點的名稱。  一份程式碼路徑表示的呼叫堆疊。  
  
## 請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)