---
title: IDebugDisassemblyStream2：： Read |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202999"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

從反組解碼資料流程中的目前位置開始讀取指示。  
  
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
 在要拆解的指令數目。 此值也是陣列的最大長度 `prgDisassembly` 。  
  
 `dwFields`  
 在 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) 列舉中的旗標組合，表示要填寫的欄位 `prgDisassembly` 。  
  
 `pdwInstructionsRead`  
 擴展傳回實際拆解的指令數目。  
  
 `prgDisassembly`  
 擴展 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 結構的陣列，這個陣列會填入拆解程式碼，每個拆解指令都有一個結構。 這個陣列的長度是由參數所決定 `dwInstructions` 。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 您可以藉由呼叫 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) 方法，取得目前範圍內可用的最大指令數目。  
  
 您可以藉由呼叫 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) 方法來變更從中讀取下一個指令的目前位置。  
  
 `DSF_OPERANDS_SYMBOLS`旗標可以新增至 `DSF_OPERANDS` 參數中的旗 `dwFields` 標，以指出在反彙編指令時應使用符號名稱。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
