---
title: IDebugMemoryBytes2::ReadAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16c5df12b268fb53ebd5b6174cbf9225a868f048
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023625"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
讀取指定的位置開始的位元組序列。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pStartContext`  
 [in][IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件，指定要從何處開始讀取的位元組。  
  
 `dwCount`  
 [in]要讀取的位元組數目。 也會指定的長度`rgbMemory`陣列。  
  
 `rgbMemory`  
 [in、 out]實際讀取的位元組填入的陣列。  
  
 `pdwRead`  
 [out]傳回實際讀取的連續位元組數目。  
  
 `pdwUnreadable`  
 [in、 out]傳回無法讀取的位元組數目。 可能是 null 值，如果用戶端不願就無法讀取的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果要求 100 個位元組和前 50 個可讀取、 後 20，則無法讀取，而且其餘 30 是可讀取，則這個方法會傳回：  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 在此情況下，因為`*pdwRead + *pdwUnreadable < dwCount`，呼叫端必須進行額外的呼叫來讀取原始要求的 100 個剩餘的 30 個位元組而[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)傳入物件`pStartContext`必須進階參數由 70。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)