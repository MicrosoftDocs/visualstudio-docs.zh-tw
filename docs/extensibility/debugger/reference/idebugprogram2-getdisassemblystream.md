---
title: IDebugProgram2::GetDisassemblyStream |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5b991a877f91b9324b6535fb3b79b082cd901c2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
取得此程式或此程式的一部分反組譯碼資料流。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDisassemblyStream(   
   DISASSEMBLY_STREAM_SCOPE   dwScope,  
   IDebugCodeContext2*        pCodeContext,  
   IDebugDisassemblyStream2** ppDisassemblyStream  
);  
```  
  
```csharp  
int GetDisassemblyStream(   
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,  
   IDebugCodeContext2             pCodeContext,  
   out IDebugDisassemblyStream2   ppDisassemblyStream  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwScope`  
 [in]指定的值從[DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)定義反組譯碼資料流的範圍列舉型別。  
  
 `pCodeContext`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件，代表要從何處開始反組譯碼資料流的位置。  
  
 `ppDisassemblyStream`  
 [out]傳回[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)代表反組譯碼資料流的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_DISASM_NOTSUPPORTED`這個特定的架構不支援反組譯碼，則為。  
  
## <a name="remarks"></a>備註  
 如果`dwScopes`參數具有`DSS_HUGE`旗標[DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)列舉集合，則反組譯碼預期會傳回大量的反組譯碼指令，例如，整個檔案或模組。 如果`DSS_HUGE`未設定旗標，則必須反組譯碼侷限於小型區域中，通常是，單一函式。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)