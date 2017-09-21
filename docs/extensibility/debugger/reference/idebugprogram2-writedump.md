---
title: "IDebugProgram2::WriteDump | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::WriteDump"
helpviewer_keywords: 
  - "IDebugProgram2::WriteDump"
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgram2::WriteDump
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

寫入檔案傾印。  
  
## 語法  
  
```cpp#  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```c#  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### 參數  
 `DumpType`  
 \[in\]介於[DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md)列舉型別，指定傾印，型別，例如，短或長時間。  
  
 `pszDumpUrl`  
 \[in\]要寫入傾印的 URL。  這通常是在表單中的 `file://c:\path\filename.ext`，不過也可能是任何有效的 URL。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 目前的堆疊框架、 堆疊本身、 在該程式，而且可能是由程式所擁有的任何記憶體上執行的執行緒的清單，通常會包括程式傾印。  
  
## 請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)