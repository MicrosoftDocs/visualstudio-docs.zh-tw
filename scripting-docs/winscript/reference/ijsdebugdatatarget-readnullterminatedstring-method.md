---
title: 'Ijsdebugdatatarget:: Readnullterminatedstring 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a681dcedf873f0cb96f47b14278f47271cd43ec8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093323"
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