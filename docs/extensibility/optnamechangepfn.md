---
title: "OPTNAMECHANGEPFN | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OPTNAMECHANGEPFN"
helpviewer_keywords: 
  - "OPTNAMECHANGEPFN 回呼函式"
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這是在呼叫中指定的回呼函式 [SccSetOption](../extensibility/sccsetoption-function.md) \(使用選項 `SCC_OPT_NAMECHANGEPFN`\) 和用來通訊名稱所做的變更原始檔控制外掛程式回 IDE。  
  
## 簽章  
  
```cpp#  
typedef void (*OPTNAMECHANGEPFN)( LPVOID pvCallerData, LPCSTR pszOldName, LPCSTR pszNewName );  
```  
  
## 參數  
 pvCallerData  
 \[\] in在前一次呼叫中指定的使用者值 [SccSetOption](../extensibility/sccsetoption-function.md) \(使用選項 `SCC_OPT_USERDATA`\)。  
  
 pszOldName  
 \[\] in檔案的原始名稱。  
  
 pszNewName  
 \[\] in檔案的名稱已重新命名為。  
  
## 傳回值  
 無。  
  
## 備註  
 如果檔案已重新命名原始檔控制作業期間，原始檔控制外掛程式會通知名稱變更，透過此回呼相關的 IDE。  
  
 如果在 IDE 中不支援此回呼，它不會呼叫 [SccSetOption](../extensibility/sccsetoption-function.md) 加以指定。 如果外掛程式不支援此回呼，則會傳回 `SCC_E_OPNOTSUPPORTED` 從 `SccSetOption` 時，IDE 會嘗試設定回呼函式。  
  
## 請參閱  
 [IDE 所實作的回呼函式](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)