---
title: 'Ijsdebugprocess:: Createstackwalker 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateStackWalker
apilocation:
- jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f9c39163eae1f3a9bad15697bbc5621661bc781
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088279"
---
# <a name="ijsdebugprocesscreatestackwalker-method"></a>IJsDebugProcess::CreateStackWalker 方法
堆疊查核器的 factory 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### <a name="parameters"></a>參數  
 `threadId`  
 [in]執行緒 id。  
  
 `ppStackWalker`  
 [out]新的堆疊查核器物件。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 如果執行緒在其上沒有 JavaScript，則傳回 E_JsDEBUG_UNKNOWN_THREAD。 目標處理序停止時，可能只呼叫這個方法。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugProcess 介面](../../winscript/reference/ijsdebugprocess-interface.md)