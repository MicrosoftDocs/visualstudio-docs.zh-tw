---
title: "Ijsdebugdatatarget:: Getthreadcontext 方法 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.GetThreadContext
apilocation: jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e2f858c66eda2ad09b04d7beab776c793b6f195
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext 方法
擷取內容提供執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `threadId`  
 [in]目標處理序中執行的執行緒。  
  
 `contextFlags`  
 [in]指定內容的旗標。 這是與內容的 ContextFlags 欄位 （如需詳細資訊，請參閱 winnt.h，搜尋 CONTEXT_ALL） 相同。  
  
 `contextSize`  
 [in]PContext 所指定的緩衝區大小。  
  
 `pContext`  
 [out]接收到 pContext 所指定的緩衝區的平台專屬內容結構。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)