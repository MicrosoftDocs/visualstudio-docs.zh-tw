---
title: "Ienumjsstackframes:: Next 方法 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumJsStackFrames.Next
apilocation: jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2068bd130e7eb03747b89e2ba107019aa1cd458
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ienumjsstackframesnext-method"></a>IEnumJsStackFrames::Next 方法
取得指定的框架數。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [out]要儲存框架的陣列。  
  
 `pcFetched`  
 [out]傳回的畫面格數目。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IEnumJsStackFrames 介面](../../winscript/reference/ienumjsstackframes-interface.md)