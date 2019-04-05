---
title: IDebugDisassemblyStream2::Read |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 520c801a0603f2c6d3228ae95ad144827eac0088
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939892"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

讀取從目前的位置，在反組譯碼資料流中的指示。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```csharp  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwInstructions`  
 [in]反組譯的指令數目。 此值也是最大長度`prgDisassembly`陣列。  
  
 `dwFields`  
 [in]從旗標的組合[DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)列舉，指出欄位`prgDisassembly`要填寫。  
  
 `pdwInstructionsRead`  
 [out]傳回實際解譯的指令的數目。  
  
 `prgDisassembly`  
 [out]陣列[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)會填入反組譯碼中，反組譯指示每一個結構的結構。 這個陣列的長度取決於`dwInstructions`參數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 可取得指示目前的範圍中的可用的最大數目，請呼叫[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)方法。  
  
 藉由呼叫可變更下一個指令會從讀取目前位置[搜尋](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)方法。  
  
 `DSF_OPERANDS_SYMBOLS`旗標可以加入至`DSF_OPERANDS`中的旗標`dwFields`參數來指出反組譯指示時，是否應使用符號名稱。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
