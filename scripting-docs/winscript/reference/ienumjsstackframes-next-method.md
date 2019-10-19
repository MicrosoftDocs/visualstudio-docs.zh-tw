---
title: IEnumJsStackFrames：： Next 方法 |Microsoft Docs
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
ms.openlocfilehash: c24ef399a7b12a1bffe8313c09be47d6a6a3b6c8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575525"
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
 在要取得的框架數目。  
  
 `pFrames`  
 脫銷要儲存框架的陣列。  
  
 `pcFetched`  
 脫銷傳回的畫面格數目。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IEnumJsStackFrames 介面](../../winscript/reference/ienumjsstackframes-interface.md)