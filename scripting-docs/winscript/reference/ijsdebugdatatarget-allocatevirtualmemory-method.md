---
title: 'Ijsdebugdatatarget:: Allocatevirtualmemory 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.AllocateVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65b29bbf9a3405bcfab779bd877f798a863538d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728398"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory 方法
保留和/或認可的目標處理序的虛擬位址空間中的記憶體區域。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>參數  
 `address`  
 [in]目標處理序應該認可或保留的記憶體中位址。 這個值通常是的零，其中案例系統會選擇一個位址。  
  
 `size`  
 [in]配置，以位元組為單位的記憶體區域的大小。 系統會自動四捨五入至下一個分頁界限。  
  
 `allocationType`  
 [in]表示配置給執行類型。 這通常是 MEM_COMMIT &#124;MEM_RESERVE (0x3000) 會保留並認可在一個步驟中的配置。  
  
 `pageProtection`  
 [in]要配置的頁面區域記憶體保護。 如果頁面會被認可，您可以指定任何其中一個記憶體保護常數 （例如 PAGE_READWRITE、 PAGE_EXECUTE）。  
  
 `pAllocatedAddress`  
 [out]頁面的配置區域的基底位址。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 除非使用 MEM_RESET 函式會初始化為零，配置的記憶體。 如需詳細資訊，請參閱 VirtualAlloc Win32 API。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)