---
title: 'Ienumjsstackframes:: Next 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumJsStackFrames.Next
apilocation:
- jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1838d6494311502faf99d86c80e0a74ded4c6e5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092400"
---
# <a name="ienumjsstackframesnext-method"></a>IEnumJsStackFrames::Next 方法
取得指定的框架數。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cFrameCount`  
 [in]若要取得的畫面格數目。  
  
 `pFrames`  
 [out]要儲存畫面格的陣列。  
  
 `pcFetched`  
 [out]傳回的畫面格數目。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IEnumJsStackFrames 介面](../../winscript/reference/ienumjsstackframes-interface.md)