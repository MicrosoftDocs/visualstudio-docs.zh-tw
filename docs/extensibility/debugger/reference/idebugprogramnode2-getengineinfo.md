---
title: "IDebugProgramNode2::GetEngineInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::GetEngineInfo"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetEngineInfo"
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramNode2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得名稱和執行程式的偵錯引擎 \(DE\) 的識別項。  
  
## 語法  
  
```cpp#  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```c#  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### 參數  
 `pbstrEngine`  
 \[\] out傳回值為目前執行程式 DE \(c \+ \+ 特有： 這可能是 null 指標，表示呼叫者不想要的引擎的名稱\)。  
  
 `pguidEngine`  
 \[\] out傳回 DE 執行程式的全域唯一識別項 \(c \+ \+ 特有： 這可能是 null 指標，表示呼叫者不想要的引擎 GUID\)。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)