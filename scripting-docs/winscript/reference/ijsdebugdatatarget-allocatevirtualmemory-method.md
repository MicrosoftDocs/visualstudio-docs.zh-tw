---
title: IJsDebugDataTarget：： AllocateVirtualMemory 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 30ad8a3eb277823271fbfb4c2e10364b8602775c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577647"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory 方法
保留及/或認可目標進程的虛擬位址空間內的記憶體區域。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
 在目標進程內應認可或保留記憶體的位址。 這個值通常是零，在這種情況下，系統會選擇位址。  
  
 `size`  
 在要配置的記憶體區域大小（以位元組為單位）。 系統會自動進位到下一個頁面界限。  
  
 `allocationType`  
 在表示要執行的配置類型。 這通常是 MEM_COMMIT &#124; MEM_RESERVE （0x3000），會在一個步驟中保留並認可配置。  
  
 `pageProtection`  
 在要配置之頁面區域的記憶體保護。 如果正在認可頁面，您可以指定任何一個記憶體保護常數（例如，PAGE_READWRITE、PAGE_EXECUTE）。  
  
 `pAllocatedAddress`  
 脫銷配置的頁面區域基底位址。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 除非使用 MEM_RESET，否則函式會將它所配置的記憶體初始化為零。 如需詳細資訊，請參閱 VirtualAlloc WIN32 API。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)