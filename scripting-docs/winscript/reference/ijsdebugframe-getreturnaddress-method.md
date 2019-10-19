---
title: IJsDebugFrame：： GetReturnAddress 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetReturnAddress
apilocation:
- jscript9diag.dll
ms.assetid: 7f10c1d6-d7b9-402e-9020-04cded37f9d3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 802355bdef386ceb252e776f8c6e798df18c9253
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577353"
---
# <a name="ijsdebugframegetreturnaddress-method"></a>IJsDebugFrame::GetReturnAddress 方法
取得在框架的 ' start ' （請參閱 GetStackRange）中推送的傳回位址。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetReturnAddress(  
   UINT64 *pReturnAddress  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pReturnAddress`  
 脫銷傳回位址。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)