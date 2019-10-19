---
title: IJsDebugDataTarget：： GetTlsValue 方法 |Microsoft Docs
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
ms.openlocfilehash: eecf9acf370656d5310a03d68ed74e10671a0bc2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577597"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue 方法
對於正在進行調試的執行緒，會針對指定的 TLS 索引，抓取執行緒區域儲存區（TLS）插槽中的值。  
  
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
 在要從中讀取的目標進程中執行的執行緒。  
  
 `tlsIndex`  
 在當目標進程呼叫 TlsAlloc 函式時，所配置的 TLS 索引。  
  
 `pValue`  
 脫銷指標大小值，儲存線上程的 TLS 位置。 如果目標執行緒是32位，此值的上32位會是零。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 進程的每個執行緒都有自己的每個 TLS 索引位置。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)