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
ms.openlocfilehash: 411679a03daf27046fdcede7ff48e76212bbd2fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557942"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess 介面
提供一些常式來檢查和控制目標處理序。  
  
## <a name="syntax"></a>語法  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint 方法](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|在指定的文件的位置設定中斷點。|  
|[IJsDebugProcess::CreateStackWalker 方法](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|堆疊查核器的 factory 方法。|  
|[IJsDebugProcess::PerformAsyncBreak 方法](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|指令碼引擎置於中斷模式，使其在下一個指令碼指令上中斷。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)