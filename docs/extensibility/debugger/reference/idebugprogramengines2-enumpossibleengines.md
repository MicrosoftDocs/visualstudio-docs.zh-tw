---
title: "IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEngines2::EnumPossibleEngines"
helpviewer_keywords: 
  - "IDebugProgramEngines2::EnumPossibleEngines"
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

傳回所有可能的偵錯引擎 \(DE\) 均可以偵錯本程式之的 Guid。  
  
## 語法  
  
```cpp#  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```c#  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### 參數  
 `celtBuffer`  
 \[in\]要傳回的 DE Guid 數目。  這也會指定最大`rgguidEngines`陣列。  
  
 `rgguidEngines`  
 輸入 \[、 輸出\]DE Guid，以填入的陣列。  
  
 `pceltEngines`  
 \[\] out傳回所傳回的 DE Guid 的實際數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  傳回 \[c \+ \+\] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)`或 \[C\#\] 0x8007007A，如果緩衝區不夠大。  
  
## 備註  
 若要判斷有多少引擎，呼叫這個方法一次是使用`celtBuffer`參數設為 0 和`rgguidEngines`參數設為 null 值。  這會傳回`HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` \(0x8007007A 的 C\#\)，以及`pceltEngines`參數會傳回所需的緩衝區大小。  
  
## 請參閱  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)