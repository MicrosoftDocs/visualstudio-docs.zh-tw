---
title: 'Ijsdebugdatatarget:: Readnullterminatedstring 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadNullTerminatedString
apilocation:
- jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 178a2d3705e4904de9253c02319f6ba94e567d76
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62582359"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>IJsDebugDataTarget::ReadNullTerminatedString 方法
從目標讀取指定的字元數。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>參數  
 `address`  
 [in]要讀取的位址。  
  
 `characterSize`  
 [in] 字串中的每個字元的大小  
  
 `maxCharacters`  
 [in]要讀取的字元數目上限。 maxCharacters 應是合理的。 大於 128 MB 的記憶體的所有要求都會都失敗。  如果字串大於 maxCharacters，則結果字串會截斷 maxCharacters 之後遭截斷。  
  
 `pString`  
 [out]從目標讀取 BSTR。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 如果截斷，則傳回 S_FALSE。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)