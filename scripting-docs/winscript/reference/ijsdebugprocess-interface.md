---
title: IJsDebugProcess 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9200515b2c975fb1fa5b2acda7c261cb684d85b4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577337"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess 介面
提供用來檢查及控制目標進程的常式。  
  
## <a name="syntax"></a>語法  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|[屬性]|描述|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint 方法](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|在指定的檔位置設定中斷點。|  
|[IJsDebugProcess::CreateStackWalker 方法](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|堆疊查看的 Factory 方法。|  
|[IJsDebugProcess::PerformAsyncBreak 方法](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|將腳本引擎放在中斷模式下，使其在下一個腳本指示中斷。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)