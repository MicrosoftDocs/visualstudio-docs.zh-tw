---
title: "IDebugProcess3::GetHostingProcessLanguage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::GetHostingProcessLanguage"
helpviewer_keywords: 
  - "IDebugProcess3::GetHostingProcessLanguage"
ms.assetid: 52fca002-a9ef-43b1-9192-afbe7bb59ad4
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess3::GetHostingProcessLanguage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會傳回`GUID`代表此程序的語言所設定，呼叫[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)。  
  
## 語法  
  
```cpp  
HRESULT GetHostingProcessLanguage(  
   GUID* pguidLang  
);  
```  
  
```c#  
int GetHostingProcessLanguage(  
   out Guid pguidLang  
);  
```  
  
#### 參數  
 `pguidLang`  
 \[\] out`GUID`這項程序使用的語言。  `GUID_NULL`\(C \+ \+\) 或`Guid.Empty` \(C\#\) 表示的語言並未設定。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)