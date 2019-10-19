---
title: IJsDebugDataTarget：： GetThreadCoNtext 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetThreadContext
apilocation:
- jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da5722553b448605129adcf32cfaa52e2dc76352
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577651"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext 方法
抓取指定執行緒的內容。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `threadId`  
 在在目標進程中執行的執行緒。  
  
 `contextFlags`  
 在指定內容旗標。 這與內容的 CoNtextFlags 欄位相同（如需詳細資訊，請參閱 winnt. h，搜尋 CONTEXT_ALL）。  
  
 `contextSize`  
 在PCoNtext 所指定的緩衝區大小。  
  
 `pContext`  
 脫銷將平臺特定的內容結構接收到 pCoNtext 所指定的緩衝區。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)