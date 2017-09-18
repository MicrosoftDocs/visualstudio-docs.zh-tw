---
title: "IDebugDisassemblyStream2::Read | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::Read"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Read"
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

讀取指令從 \[反組譯碼資料流的目前位置開始。  
  
## 語法  
  
```cpp#  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```c#  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### 參數  
 `dwInstructions`  
 \[in\]反組譯的指令數目。  這個值也是最大長度`prgDisassembly`陣列。  
  
 `dwFields`  
 \[in\]從的旗標組合[DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)列舉型別，會指出哪一個欄位的`prgDisassembly`都必須填寫。  
  
 `pdwInstructionsRead`  
 \[\] out傳回實際反組譯的指令的數目。  
  
 `prgDisassembly`  
 \[\] out陣列的[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)會填入這些反組譯程式碼中，反組譯指令每一個結構的結構。  此陣列的長度取決於`dwInstructions`參數。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 可取得指令得以在目前範圍中的最大數目，藉由呼叫[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)方法。  
  
 藉由呼叫變更目前的位置的下一個指令會從讀取[搜尋](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)方法。  
  
 `DSF_OPERANDS_SYMBOLS`旗標可以加入至`DSF_OPERANDS`中加上旗標`dwFields`參數，以指示時反組譯的指示應該使用的符號名稱。  
  
## 請參閱  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [搜尋](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)