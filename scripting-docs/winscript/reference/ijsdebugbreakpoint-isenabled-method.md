---
title: IJsDebugBreakPoint：： IsEnabled 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.IsEnabled
apilocation:
- jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25d66b7f8691a74eac77e9a90ec610fa21ec688e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577663"
---
# <a name="ijsdebugbreakpointisenabled-method"></a>IJsDebugBreakPoint::IsEnabled 方法
判斷中斷點是否已啟用。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pIsEnabled`  
 脫銷如果已啟用中斷點，則傳回 true;否則，會傳回 false。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 如果在已刪除的中斷點上呼叫，則會傳回 E_UNEXPECTED。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IJsDebugBreakPoint 介面](../../winscript/reference/ijsdebugbreakpoint-interface.md)