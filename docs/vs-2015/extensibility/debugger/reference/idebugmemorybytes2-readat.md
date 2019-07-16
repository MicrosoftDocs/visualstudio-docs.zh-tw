---
title: IDebugMemoryBytes2::ReadAt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f10dc6e9e00e2b7f66722f3c89b74bb14e45fdbe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180589"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

讀取指定的位置開始的位元組序列。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
