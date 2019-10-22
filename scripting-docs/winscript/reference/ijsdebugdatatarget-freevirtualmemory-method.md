---
title: IJsDebugDataTarget：： FreeVirtualMemory 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.FreeVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 835302249e95c89625c07c6d1ef3d7cbaf2905e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577613"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory 方法
釋放和（或）解除鎖定目標進程之虛擬位址空間內的記憶體區域。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>參數  
 `address`  
 在目標進程內應釋放記憶體的位址。  
  
 `size`  
 在要 offerreclaim11 取消認可的位元組數。 若要釋放記憶體的區域，此值必須為零。  
  
 `freeType`  
 在表示要執行的免費作業類型。 這通常是 MEM_RELEASE （0x8000），它會釋放指定的頁面區域。 在作業之後，頁面會處於 [免費] 狀態。 您可以改為使用 MEM_DECOMMIT （0x4000）來 offerreclaim11 取消認可頁面，而不需要釋放它們。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 VirtualFree WIN32 API。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)