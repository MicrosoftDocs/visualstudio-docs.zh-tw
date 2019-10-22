---
title: IJsDebug：： OpenVirtualProcess 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebug.OpenVirtualProcess
apilocation:
- jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3de39beb28a68ec3b8e0d76b17a7e914a464ecfe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577752"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess 方法
用來建立新虛擬進程物件的 Factory 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>參數  
 `processId`  
 在要附加偵錯工具的處理序識別碼。  
  
 `runtimeJsBaseAddress`  
 在JavaScript 執行時間載入目標進程的基底位址。  
  
 `pDataTarget`  
 在偵錯工具提供的介面，可查詢進程的狀態。  
  
 `ppProcess`  
 脫銷新的 debug 進程物件  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 如果 Jscript9diag 和 Jscript9.dll 不相符，則傳回 E_JsDEBUG_MISMATCHED_RUNTIME。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IJsDebug 介面](../../winscript/reference/ijsdebug-interface.md)