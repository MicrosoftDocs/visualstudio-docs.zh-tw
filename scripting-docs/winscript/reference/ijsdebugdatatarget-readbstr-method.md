---
title: "Ijsdebugdatatarget:: Readbstr 方法 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.ReadBSTR
apilocation: jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85fbdb556b59c67610ad65b7e1f056399ad6da58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetreadbstr-method"></a>IJsDebugDataTarget::ReadBSTR 方法
讀取偵錯目標的 BSTR。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>參數  
 `address`  
 [in]要讀取的位址。  
  
 `pString`  
 [out]BSTR 讀取偵錯目標。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 如果位址不正確，請傳回 E_JsDEBUG_INVALID_MEMORY_ADDRESS。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)