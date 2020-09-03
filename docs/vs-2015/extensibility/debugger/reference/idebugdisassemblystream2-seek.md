---
title: IDebugDisassemblyStream2：： Seek |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d774cc0bf6bca1278423249960bbc5233aa6ad37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203021"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

移動反組解碼資料流程中的讀取指標，指定的指示數目相對於指定的位置。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```csharp  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwSeekStart`  
 在 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) 列舉中的值，這個值會指定開始搜尋進程的相對位置。  
  
 `pCodeContext`  
 在代表搜尋作業相對的程式碼內容的 [IDebugCodeCoNtext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 物件。 只有在時才會使用這個參數 `dwSeekStart`  =  `SEEK_START_CODECONTEXT` ; 否則會忽略此參數，而且可以是 null 值。  
  
 `uCodeLocationId`  
 在搜尋作業相對的程式碼位置識別碼。 如果為，則會使用這個參數 `dwSeekStart`  =  `SEEK_START_CODELOCID` ; 否則會忽略此參數，而且可以設定為0。 如需程式碼位置識別碼的描述，請參閱 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) 方法的備註一節。  
  
 `iInstructions`  
 在要移動的指令數目，相對於中指定的位置 `dwSeekStart` 。 這個值可以是負數，以向後移動。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果搜尋位置是指向可用指令清單以外的某個點，則會傳回。 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果搜尋的位置早于清單開頭的位置，則讀取位置會設定為清單中的第一個指令。 如果看到的位置是清單結尾之後的位置，則讀取位置會設定為清單中的最後一個指令。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeCoNtext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
