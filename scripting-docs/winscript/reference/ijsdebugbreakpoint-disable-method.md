---
title: IJsDebugBreakPoint：:D 停用方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.Disable
apilocation:
- jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51e4be2abc8b5a507e091b330de1779cfb14b57e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577728"
---
# <a name="ijsdebugbreakpointdisable-method"></a>IJsDebugBreakPoint::Disable 方法
停用中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Disable(void);  
```  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 如果在已刪除的中斷點上呼叫，則會傳回 E_UNEXPECTED。 如果在已停用的中斷點上呼叫，則會傳回 S_FALSE。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IJsDebugBreakPoint 介面](../../winscript/reference/ijsdebugbreakpoint-interface.md)