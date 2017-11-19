---
title: "Ijsdebugbreakpoint:: Isenabled 方法 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJSDebugBreakPoint.IsEnabled
apilocation: jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb7ab887b8e3442a0c38ea403ad43bdea10cdd66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugbreakpointisenabled-method"></a>IJsDebugBreakPoint::IsEnabled 方法
判斷是否啟用中斷點。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pIsEnabled`  
 [out]如果啟用中斷點，則傳回 true反之則傳回 false。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 如果已刪除的中斷點上呼叫會傳回 E_UNEXPECTED。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugBreakPoint 介面](../../winscript/reference/ijsdebugbreakpoint-interface.md)