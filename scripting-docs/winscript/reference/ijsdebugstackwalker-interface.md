---
title: IJsDebugStackWalker 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d06af2c509339d9499f66e1f267c54c69951e225
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977808"
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker 介面
表示指定之執行緒的堆疊查核器。  
  
## <a name="syntax"></a>語法  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IJsDebugStackWalker::GetNext 方法](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|取得下一個畫面格。|  
  
## <a name="remarks"></a>備註  
 堆疊查核器只能建立目標已停止，而一旦目標處理序已再繼續執行，就不正確。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)