---
title: IJsDebugStackWalker 介面 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbea11bf1188d148818ea8a082bceec76c704c2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728548"
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker 介面
表示指定之執行緒的堆疊查核器。  
  
## <a name="syntax"></a>語法  
  
```  
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IJsDebugStackWalker::GetNext 方法](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|取得下一個畫面格。|  
  
## <a name="remarks"></a>備註  
 雖然目標已停止，而不正確的一旦目標處理序繼續一次只能建立堆疊 walkers。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)