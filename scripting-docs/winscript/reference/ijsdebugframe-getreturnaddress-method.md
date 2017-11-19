---
title: "Ijsdebugframe:: Getreturnaddress 方法 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.GetReturnAddress
apilocation: jscript9diag.dll
ms.assetid: 7f10c1d6-d7b9-402e-9020-04cded37f9d3
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9d2b78f049a080f70b30edb82af1066817f6adb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframegetreturnaddress-method"></a>IJsDebugFrame::GetReturnAddress 方法
取得在 'start' 推入的傳回位址 （請參閱 GetStackRange） 的框架。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetReturnAddress(  
   UINT64 *pReturnAddress  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pReturnAddress`  
 [out]傳回的位址。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)