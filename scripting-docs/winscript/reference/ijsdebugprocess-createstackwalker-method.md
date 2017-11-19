---
title: "Ijsdebugprocess:: Createstackwalker 方法 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugProcess.CreateStackWalker
apilocation: jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66ca7594f4e3c6ef44aa8cde1d92f17d46a9aa30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugprocesscreatestackwalker-method"></a>IJsDebugProcess::CreateStackWalker 方法
堆疊查核器的 factory 方法。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### <a name="parameters"></a>參數  
 `threadId`  
 [in]執行緒識別碼。  
  
 `ppStackWalker`  
 [out]新的堆疊查核器物件。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 如果執行緒在其上沒有 JavaScript，傳回 E_JsDEBUG_UNKNOWN_THREAD。 目標處理序停止時，只會呼叫這個方法。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugProcess 介面](../../winscript/reference/ijsdebugprocess-interface.md)