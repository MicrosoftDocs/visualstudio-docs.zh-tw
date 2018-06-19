---
title: 'Ijsdebugdatatarget:: Gettlsvalue 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4205adfb24a1a64d4e90f3fdcaf5a5ecbc4028de
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727878"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue 方法
正在進行偵錯的執行緒，擷取指定的 TLS 索引執行緒區域儲存區 (TLS) 插槽中的值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `threadId`  
 [in]讀取從目標處理序中執行的執行緒。  
  
 `tlsIndex`  
 [in]目標處理序呼叫 TlsAlloc 函式時所配置之 TLS 索引。  
  
 `pValue`  
 [out]指標大小的值儲存在執行緒的 TLS 插槽中。 目標執行緒是 32 位元，如果上層 32 位元的這個值將是零。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 處理序的每個執行緒有它自己的 TLS 中的每個索引的位置。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)