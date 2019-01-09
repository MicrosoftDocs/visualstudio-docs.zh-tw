---
title: JsDebugReadMemoryFlags 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bef1f16ebcf678452f2fe4b0df3ade6350120f05
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094025"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>JsDebugReadMemoryFlags 列舉
旗標，用於指定讀取記憶體時的行為。  
  
## <a name="syntax"></a>語法  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>成員  
  
### <a name="values"></a>值  
  
|名稱|描述|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|表示呼叫端想要只有一部分記憶體讀取成功的讀取的作業。 如果這個屬性設定，引發 E_JsDEBUG_INVALID_MEMORY_ADDRESS 錯誤將只是 'Address' 無效。 如果清除這個旗標，無法讀取要求的任何的記憶體部分時，將會引發 E_JsDEBUG_INVALID_MEMORY_ADDRESS 錯誤。|  
|`None`|表示呼叫端，想 readmemory 的預設行為。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)