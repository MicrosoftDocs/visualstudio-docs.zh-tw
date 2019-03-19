---
title: 'Ienumjsstackframes:: Next 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 94e3f478654fadec152aba0690a5474ebbfe02f5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159058"
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