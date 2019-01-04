---
title: IDebugProgramEngines2::EnumPossibleEngines |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b3ebf30c4152e03a72626b96cfd51b0341494ccb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891381"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
傳回所有可能的偵錯引擎 (DE) 可以偵錯此程式的 Guid。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```csharp  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celtBuffer`  
 [in]要傳回的 DE Guid 數目。 這也會指定的大小上限`rgguidEngines`陣列。  
  
 `rgguidEngines`  
 [in、 out]要填入的 DE Guid 的陣列。  
  
 `pceltEngines`  
 [out]傳回 DE Guid 所傳回的實際數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 傳回 [c + +]`HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)`或 [C#] 0x8007007A 如果緩衝區不夠大。  
  
## <a name="remarks"></a>備註  
 若要判斷有多少引擎，呼叫這個方法一次`celtBuffer`參數設定為 0 和`rgguidEngines`參數設定為 null 的值。 這會傳回`HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)`(適用於 C# 0x8007007A)，而`pceltEngines`參數會傳回所需的緩衝區大小。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)