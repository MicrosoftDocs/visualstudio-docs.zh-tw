---
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: b021edcf63afc852a3e8a007085e06292c49aee0
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Returns the GUIDs for all the possible debug engines (DE) that can debug this program.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```cs  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `celtBuffer`  
 [in] The number of DE GUIDs to return. This also specifies the maximum size of the `rgguidEngines` array.  
  
 `rgguidEngines`  
 [in, out] An array of DE GUIDs to be filled in.  
  
 `pceltEngines`  
 [out] Returns the actual number of DE GUIDs that are returned.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code. Returns [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` or [C#] 0x8007007A if the buffer is not large enough.  
  
## <a name="remarks"></a>Remarks  
 In order to determine how many engines there are, call this method once with the `celtBuffer` parameter set to 0 and the `rgguidEngines` parameter set to a null value. This returns `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A for C#), and the `pceltEngines` parameter returns the necessary size of the buffer.  
  
## <a name="see-also"></a>See Also  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
