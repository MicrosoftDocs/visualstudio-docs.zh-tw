---
title: JsDebugReadMemoryFlags 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugReadMemoryFlags
apilocation:
- jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1757678f20a01221ae46e1535d3190cd463d724
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571707"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>JsDebugReadMemoryFlags 列舉
旗標，用於指定讀取記憶體時的行為。  
  
## <a name="syntax"></a>語法  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Members  
  
### <a name="values"></a>值  
  
|[屬性]|描述|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|表示呼叫端想要在只有部分記憶體讀取成功時，讀取作業才會成功。 如果設定這個，只有當 ' Address ' 無效時，才會引發 E_JsDEBUG_INVALID_MEMORY_ADDRESS 錯誤。 如果清除此旗標，當要求的記憶體有任何部分無法讀取時，就會引發 E_JsDEBUG_INVALID_MEMORY_ADDRESS 錯誤。|  
|`None`|表示呼叫端想要 ReadMemory 的預設行為。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)