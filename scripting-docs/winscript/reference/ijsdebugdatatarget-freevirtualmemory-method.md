---
title: 'Ijsdebugdatatarget:: Freevirtualmemory 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 3b53d7f80227a1c4eb0ef0293093543c09c5a367
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728738"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory 方法
釋放及/或回收的目標處理序的虛擬位址空間中的記憶體區域。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>參數  
 `address`  
 [in]目標處理序應該釋放記憶體內的位址。  
  
 `size`  
 [in]要認可的位元組數目。 若要釋放區域，這個值必須是記憶體的零。  
  
 `freeType`  
 [in]表示要執行的可用作業的類型。 這通常是 MEM_RELEASE (0x8000)，這會釋放頁面的指定的區域。 作業之後，頁面是處於可用狀態。 可以改為使用 MEM_DECOMMIT (0x4000)，才能認可頁面而未釋放它們。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 VirtualFree Win32 API。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)