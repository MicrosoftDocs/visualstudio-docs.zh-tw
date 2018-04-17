---
title: IDebugMemoryBytes2::ReadAt |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f4c71da3152394442d63c937b77e4f6538fcc1ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
讀取在指定位置開始的位元組序列。  
  
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
 [in][IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件，指定要從何處開始寫入讀取位元組。  
  
 `dwCount`  
 [in]要讀取的位元組數目。 也會指定的長度`rgbMemory`陣列。  
  
 `rgbMemory`  
 [in、 out]實際讀取填入之位元組的陣列。  
  
 `pdwRead`  
 [out]傳回實際讀取的連續位元組數目。  
  
 `pdwUnreadable`  
 [in、 out]傳回讀取的位元組數目。 可能是 null 值，如果用戶端是興趣無法讀取的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果要求 100 個位元組和第 50 可讀取、 下一步 20，則無法讀取，而且其餘 30 是可讀取，這個方法會傳回：  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 在此情況下，因為`*pdwRead + *pdwUnreadable < dwCount`，呼叫端必須進行額外的呼叫來讀取剩餘的原始要求的 100 30 個位元組和[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件傳入`pStartContext`必須進階參數由 70。  
  
## <a name="see-also"></a>請參閱  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)