---
title: "POPDIRLISTFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "POPLISTFUNC"
helpviewer_keywords: 
  - "POPDIRLISTFUNC 回呼函式"
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這是提供給回呼函式 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 函式來更新目錄以及 \(選擇性\) 若要找出哪些是原始檔控制下的檔案名稱的集合。  
  
 `POPDIRLISTFUNC` 應該呼叫回呼，僅適用於這些目錄和檔案名稱 \(在清單中指定給 `SccPopulateDirList` 函式\)，實際上是原始檔控制下。  
  
## 簽章  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)( LPVOID pvCallerData, BOOL bFolder, LPCSTR lpDirectoryOrFileName );  
```  
  
## 參數  
 pvCallerData  
 \[\] in提供給使用者值 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)。  
  
 bFolder  
 \[in\] `TRUE` 如果在名稱 `lpDirectoryOrFileName` 是一個目錄中; 否則名稱會是檔案名稱。  
  
 lpDirectoryOrFileName  
 \[\] in完整的本機路徑是在原始檔控制下的目錄或檔案名稱。  
  
## 傳回值  
 IDE 會傳回適當的錯誤程式碼:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|繼續處理。|  
|SCC\_I\_OPERATIONCANCELED|停止處理。|  
|SCC\_E\_xxx|任何適當的原始檔控制錯誤應該停止處理。|  
  
## 備註  
 如果 `fOptions` 參數 `SccPopulateDirList` 函式包含 `SCC_PDL_INCLUDEFILES` 旗標，清單可能包含檔案名稱，以及目錄名稱。  
  
## 請參閱  
 [IDE 所實作的回呼函式](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [錯誤代碼](../extensibility/error-codes.md)