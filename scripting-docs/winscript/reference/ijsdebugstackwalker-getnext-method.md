---
title: "Ijsdebugstackwalker:: Getnext 方法 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugStackWalker.GetNext
apilocation: jscript9diag.dll
ms.assetid: 0b124768-50d3-4a69-876c-1aa337839a4e
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 695bb6cecc2a27565dce21b4a965ad08d90d7be7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugstackwalkergetnext-method"></a>IJsDebugStackWalker::GetNext 方法
取得下一個畫面格。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetNext(  
   IJsDebugFrame **ppFrame  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppFrame`  
 [out]代表堆疊框架的物件。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 傳回 E_JsDEBUG_OUTSIDE_OF_VM 時有更多堆疊框架要列舉  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugStackWalker 介面](../../winscript/reference/ijsdebugstackwalker-interface.md)