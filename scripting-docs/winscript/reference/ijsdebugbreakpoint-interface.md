---
title: IJsDebugBreakPoint 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 791c8488-21e7-46be-b1b4-fe74117cf200
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c43d23d0ba89e6b85a3dd4da688fa89fed4dd99
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093843"
---
# <a name="ijsdebugbreakpoint-interface"></a>IJsDebugBreakPoint 介面
表示中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp
IJsDebugBreakPoint : public IUnknown;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IJsDebugBreakPoint::Delete 方法](../../winscript/reference/ijsdebugbreakpoint-delete-method.md)|刪除中斷點。|  
|[IJsDebugBreakPoint::Disable 方法](../../winscript/reference/ijsdebugbreakpoint-disable-method.md)|停用中斷點。|  
|[IJsDebugBreakPoint::Enable 方法](../../winscript/reference/ijsdebugbreakpoint-enable-method.md)|啟用中斷點。|  
|[IJsDebugBreakPoint::GetDocumentPosition 方法](../../winscript/reference/ijsdebugbreakpoint-getdocumentposition-method.md)|傳回陳述式的中斷點已繫結的位置。|  
|[IJsDebugBreakPoint::IsEnabled 方法](../../winscript/reference/ijsdebugbreakpoint-isenabled-method.md)|決定是否啟用中斷點。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)