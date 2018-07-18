---
title: 'Ijsdebugdatatarget:: Writememory 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ed562c1cbdd645da6cca87e45f272c25f8bc0d4b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727898"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>IJsDebugDataTarget::WriteMemory 方法
讀取目標處理序的記憶體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>參數  
 `address`  
 [in]要從中寫入目標處理序記憶體基底位址。  
  
 `pMemory`  
 [in]要寫入指定的處理序的位址空間中的資料。  
  
 `size`  
 [in]要寫入處理序的位元組數目。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 資料傳輸發生之前，系統會確認基底位址與指定大小的記憶體中的所有資料存取進行寫入存取，並不能存取，如果函式就會引發 E_JsDEBUG_INVALID_MEMORY_ADDRESS 錯誤。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)