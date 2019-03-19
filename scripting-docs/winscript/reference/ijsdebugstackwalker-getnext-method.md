---
title: 'Ijsdebugstackwalker:: Getnext 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugStackWalker.GetNext
apilocation:
- jscript9diag.dll
ms.assetid: 0b124768-50d3-4a69-876c-1aa337839a4e
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba8931a01f3afe05f791f4d89da60a9354868215
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148447"
---
# <a name="ijsdebugstackwalkergetnext-method"></a>IJsDebugStackWalker::GetNext 方法
取得下一個畫面格。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetNext(  
   IJsDebugFrame **ppFrame  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppFrame`  
 [out]物件，代表堆疊框架。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 要列舉的堆疊框架時，傳回 E_JsDEBUG_OUTSIDE_OF_VM  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugStackWalker 介面](../../winscript/reference/ijsdebugstackwalker-interface.md)