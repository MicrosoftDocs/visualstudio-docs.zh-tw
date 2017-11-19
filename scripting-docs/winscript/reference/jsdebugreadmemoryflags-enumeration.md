---
title: "JsDebugReadMemoryFlags 列舉 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: JsDebugReadMemoryFlags
apilocation: jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7efb5170bf0314e95b1acded39a897c2236a29ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>JsDebugReadMemoryFlags 列舉
旗標，用於指定讀取記憶體時的行為。  
  
## <a name="syntax"></a>語法  
  
```  
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Members  
  
### <a name="values"></a>值  
  
|名稱|說明|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|表示呼叫端想讀取的作業成功，如果只有部分記憶體讀取成功。 如果這個屬性設定，如果是無效的 'Address' 只會引發 E_JsDEBUG_INVALID_MEMORY_ADDRESS 錯誤。 如果清除此旗標，如果無法讀取要求的任何的記憶體部分，將會引發 E_JsDEBUG_INVALID_MEMORY_ADDRESS 錯誤。|  
|`None`|表示呼叫端想預設行為，如 ReadMemory。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)