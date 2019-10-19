---
title: IJsDebugDataTarget：： ReadMemory 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadMemory
apilocation:
- jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84da36433cf3546b34d3e044bb113916c9798117
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572427"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory 方法
讀取目標進程的記憶體。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>參數  
 `address`  
 在要從中讀取目標進程記憶體的基底位址。  
  
 `flags`  
 在控制 ReadMemory 行為的旗標。  
  
 `pBuffer`  
 脫銷從目標進程的位址空間接收內容的緩衝區。 當失敗時，這個緩衝區的內容是未指定的。  
  
 `size`  
 在要從進程讀取的位元組數目。  
  
 `pBytesRead`  
 脫銷表示從目標進程讀取的位元組數目。 如果 JsDebugAllowPartialRead 是清除的，則在成功時，此值一律會完全等於輸入大小。 如果指定了 JsDebugAllowPartialRead，則在成功時，這個值會大於零。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 會在成功時傳回 S_OK，而失敗碼會用於任何錯誤。 如果位址無效，則會傳回 E_JsDEBUG_INVALID_MEMORY_ADDRESS。 如需詳細資訊，請參閱 JsDebugAllowPartialRead。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)