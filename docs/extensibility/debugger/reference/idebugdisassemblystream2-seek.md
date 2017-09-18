---
title: "IDebugDisassemblyStream2::Seek | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::Seek"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Seek"
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::Seek
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

將讀取的指標移至反組譯碼資料流指定數目之指示相對於指定的位置中。  
  
## 語法  
  
```cpp#  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```c#  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### 參數  
 `dwSeekStart`  
 \[in\]介於[SEEK\_START](../../../extensibility/debugger/reference/seek-start.md)列舉型別，指定開始搜尋程序的相對位置。  
  
 `pCodeContext`  
 \[in\][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件，表示搜尋作業是相對於程式碼內容。  只有當使用這個參數`dwSeekStart` \= `SEEK_START_CODECONTEXT`。 否則，這個參數會被忽略，並可為 null 值。  
  
 `uCodeLocationId`  
 \[in\]搜尋作業是相對於程式碼的位置識別碼。  如果使用這個參數`dwSeekStart` \= `SEEK_START_CODELOCID`。 否則，這個參數會被忽略，並且可以設為 0。  請參閱 \[備註\] 部份的[GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)的程式碼的位置識別碼說明的方法。  
  
 `iInstructions`  
 \[in\]移至指定的位置相對的指令數目`dwSeekStart`。  這個值可以是負向後移動。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果搜尋位置清單以外的可用指令的點。  否則，會傳回錯誤碼。  
  
## 備註  
 如果搜尋不到清單的開頭之前的位置，則會將讀取的位置設定為在清單中的第一個指令。  如果查看到的位置在清單結尾之後，則讀取的位置設至最後一個指令清單中。  
  
## 請參閱  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)