---
title: IDebugProgramEngines2：： EnumPossibleEngines |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a417fd4f0d90ffebd291179dee28a0e81f92cce9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182192"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

傳回所有可能的 debug 引擎的 Guid (DE) 可將此程式進行偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 在要傳回的解除 Guid 數目。 這也會指定陣列的大小上限 `rgguidEngines` 。  
  
 `rgguidEngines`  
 [in，out]要填入的 DE Guid 陣列。  
  
 `pceltEngines`  
 擴展傳回傳回的實際已解除 Guid 數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 如果緩衝區不夠大，則會傳回 [c + +] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` 或 [c #] 0x8007007A。  
  
## <a name="remarks"></a>備註  
 若要判斷有多少引擎存在，請呼叫這個方法一次，並將 `celtBuffer` 參數設定為0，並將 `rgguidEngines` 參數設定為 null 值。 這會傳回 `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` c # ) 的 (0x8007007A，而參數會傳回所 `pceltEngines` 需的緩衝區大小。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
