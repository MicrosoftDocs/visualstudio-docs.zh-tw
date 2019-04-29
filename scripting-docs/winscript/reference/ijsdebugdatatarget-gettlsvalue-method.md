---
title: 'Ijsdebugdatatarget:: Gettlsvalue 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetTlsValue
apilocation:
- jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 458aaab05f274983fdaf69c6e702502974665403
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62582806"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue 方法
正在進行偵錯的執行緒，擷取所指定 TLS 索引的執行緒區域儲存區 (TLS) 位置中的值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `threadId`  
 [in]從讀取目標處理序中執行的執行緒。  
  
 `tlsIndex`  
 [in]目標處理序呼叫 TlsAlloc 函式時所配置的 TLS 索引。  
  
 `pValue`  
 [out]指標大小的值是儲存在執行緒的 TLS 位置。 如果目標執行緒為 32 位元，上方 32 位元的這個值會是零。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 每個執行緒的處理程序有它自己的每個 TLS 索引的位置。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)