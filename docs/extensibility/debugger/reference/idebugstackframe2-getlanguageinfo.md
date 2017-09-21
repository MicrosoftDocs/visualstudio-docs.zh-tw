---
title: "IDebugStackFrame2::GetLanguageInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetLanguageInfo"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetLanguageInfo"
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetLanguageInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得此堆疊框架相關聯的語言。  
  
## 語法  
  
```cpp#  
HRESULT GetLanguageInfo (   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```c#  
int GetLanguageInfo (   
   ref string pbstrLanguage,  
   ref Guid   pguidLanguage  
);  
```  
  
#### 參數  
 `pbstrLanguage`  
 \[\] out傳回此堆疊框架相關聯的方法的實作語言名稱。  
  
 `pguidLanguage`  
 \[\] out傳回`GUID`的語言。  對於[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]的語言，例如，下列可能會傳回：  
  
-   `guidVBScriptLang`  
  
-   `guidJScriptLang`  
  
-   `guidCPPLang`  
  
-   `guidVBLang`  
  
-   `guidSQLLang`  
  
-   `guidScriptLang`  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)