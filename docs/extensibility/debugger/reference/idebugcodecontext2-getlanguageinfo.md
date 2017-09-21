---
title: "IDebugCodeContext2::GetLanguageInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCodeContext2::GetLanguageInfo"
helpviewer_keywords: 
  - "IDebugCodeContext2::GetLanguageInfo"
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCodeContext2::GetLanguageInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得這個程式碼內容的語言資訊。  
  
## 語法  
  
```cpp#  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```c#  
int GetLanguageInfo(   
   ref string pbstrLanguage,  
   ref Guid pguidLanguage  
);  
```  
  
#### 參數  
 `pbstrLanguage`  
 輸入 \[、 輸出\]傳回 string，其包含名稱的語言，例如"C \+ \+"。  
  
 `pguidLanguage`  
 輸入 \[、 輸出\]例如，傳回的 GUID，該語言的程式碼內容中， `guidCPPLang`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 至少一個參數必須傳回非 null 值。  
  
## 請參閱  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)