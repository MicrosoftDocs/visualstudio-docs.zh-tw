---
title: IJsDebugDataTarget：： WriteMemory 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.WriteMemory
apilocation:
- jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33cd23ad784e222f770dfd5c0e7c2d775aa55e42
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572410"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>IJsDebugDataTarget::WriteMemory 方法
讀取目標進程的記憶體。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>參數  
 `address`  
 在要從中寫入目標進程記憶體的基底位址。  
  
 `pMemory`  
 在要在指定進程的位址空間中寫入的資料。  
  
 `size`  
 在要寫入進程的位元組數目。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 在進行資料傳輸之前，系統會確認基底位址中的所有資料和指定大小的記憶體可供寫入存取，如果無法存取，函式就會引發 E_JsDEBUG_INVALID_MEMORY_ADDRESS 錯誤。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)