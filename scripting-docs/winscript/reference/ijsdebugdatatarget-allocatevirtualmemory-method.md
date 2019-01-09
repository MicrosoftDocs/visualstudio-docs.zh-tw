---
title: 'Ijsdebugdatatarget:: Allocatevirtualmemory 方法 |Microsoft Docs'
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
ms.openlocfilehash: 4eaf448e0be224f853674084a18f7aa2a6bd5ed7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086906"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory 方法
保留和 （或) 認可目標處理序虛擬位址空間中的記憶體區域。  
  
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
 [in]目標處理序應該認可或保留的記憶體內的位址。 這個值通常是的零，情況下，系統會選擇位址。  
  
 `size`  
 [in]要搜尋的配置，以位元組為單位的記憶體區域的大小。 系統將自動捨入為下一個分頁界限。  
  
 `allocationType`  
 [in]表示要執行配置的類型。 這通常是 MEM_COMMIT &#124; MEM_RESERVE (0x3000) 保留並認可配置，在一個步驟中的。  
  
 `pageProtection`  
 [in]頁面配置記憶體保護區。 如果要認可頁面，您可以指定任何一個記憶體保護常數 （例如，PAGE_READWRITE、 PAGE_EXECUTE）。  
  
 `pAllocatedAddress`  
 [out]配置的頁面區域的基底位址。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 除非 mem_reset，否則，函式會初始化為零，它會配置的記憶體。 如需詳細資訊，請參閱 VirtualAlloc Win32 API。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)