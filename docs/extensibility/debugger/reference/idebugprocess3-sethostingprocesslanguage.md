---
title: "IDebugProcess3::SetHostingProcessLanguage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::SetHostingProcessLanguage"
helpviewer_keywords: 
  - "IDebugProcess3::SetHostingProcessLanguage"
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProcess3::SetHostingProcessLanguage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會設定處理程序會裝載在\] 下的語言。  這種語言可以再用於偵錯引擎 \(DE\) 載入適當的運算式評估工具。  
  
## 語法  
  
```cpp  
HRESULT SetHostingProcessLanguage(  
   REFGUID guidLang  
);  
```  
  
```c#  
int SetHostingProcessLanguage(  
   ref Guid guidLang  
);  
```  
  
#### 參數  
 `guidLang`  
 \[in\]`GUID` DE 應該使用的語言。  指定`GUID_NULL` \(c \+ \+\) 或`Guid.Empty` \(C\#\) 將使用預設的語言 DE。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)可以用於擷取目前的語言設定。  
  
## 請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)