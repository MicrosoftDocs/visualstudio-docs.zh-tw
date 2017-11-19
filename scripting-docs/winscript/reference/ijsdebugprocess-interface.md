---
title: "IJsDebugProcess 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a81104f51ca1a66c493779146b7eaa102ea300
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess 介面
提供檢查和控制目標處理序的常式。  
  
## <a name="syntax"></a>語法  
  
```  
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint 方法](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|在指定的文件的位置設定中斷點。|  
|[IJsDebugProcess::CreateStackWalker 方法](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|堆疊查核器的 factory 方法。|  
|[IJsDebugProcess::PerformAsyncBreak 方法](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|在下一個指令碼指令中斷而造成中斷模式中將指令碼引擎。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)