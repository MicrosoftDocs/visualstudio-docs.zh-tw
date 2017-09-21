---
title: "IDebugEngine3::LoadSymbols | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::LoadSymbols"
helpviewer_keywords: 
  - "IDebugEngine3::LoadSymbols"
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugEngine3::LoadSymbols
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

\(視\) 載入符號這個偵錯引擎正在偵錯的所有模組。  
  
## 語法  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```c#  
int LoadSymbols();  
```  
  
#### 參數  
 無。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則會傳回錯誤碼。  
  
## 備註  
 這會載入這個偵錯引擎所參考的所有模組的偵錯符號。  它們沒有已被載入時，才會載入的符號。  符號會在呼叫中設定的路徑上搜尋[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)。  
  
## 請參閱  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)