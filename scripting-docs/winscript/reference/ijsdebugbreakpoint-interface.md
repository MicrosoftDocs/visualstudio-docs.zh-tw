---
title: IJsDebugBreakPoint 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 791c8488-21e7-46be-b1b4-fe74117cf200
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6bb4e12f0e08baf1842d251347f35265425b999
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577683"
---
# <a name="ijsdebugbreakpoint-interface"></a>IJsDebugBreakPoint 介面
表示中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp
IJsDebugBreakPoint : public IUnknown;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|[屬性]|描述|  
|----------|-----------------|  
|[IJsDebugBreakPoint::Delete 方法](../../winscript/reference/ijsdebugbreakpoint-delete-method.md)|刪除中斷點。|  
|[IJsDebugBreakPoint::Disable 方法](../../winscript/reference/ijsdebugbreakpoint-disable-method.md)|停用中斷點。|  
|[IJsDebugBreakPoint::Enable 方法](../../winscript/reference/ijsdebugbreakpoint-enable-method.md)|啟用中斷點。|  
|[IJsDebugBreakPoint::GetDocumentPosition 方法](../../winscript/reference/ijsdebugbreakpoint-getdocumentposition-method.md)|傳回系結中斷點之語句的位置。|  
|[IJsDebugBreakPoint::IsEnabled 方法](../../winscript/reference/ijsdebugbreakpoint-isenabled-method.md)|判斷中斷點是否已啟用。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)