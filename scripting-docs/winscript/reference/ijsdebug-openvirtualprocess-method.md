---
title: 'Ijsdebug:: Openvirtualprocess 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f5acb137337e46a6e84f7d68c9330a3ca847f2e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727358"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess 方法
用來建立新的虛擬程序物件的 factory 方法。  
  
## <a name="syntax"></a>語法  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>參數  
 `processId`  
 [in]若要附加偵錯工具的處理序識別碼。  
  
 `runtimeJsBaseAddress`  
 [in]基底位址的 JavaScript 執行階段已載入至目標處理序。  
  
 `pDataTarget`  
 [in]偵錯工具提供的介面來查詢的程序的狀態。  
  
 `ppProcess`  
 [out]新的偵錯處理程序物件  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 如果 Jscript9diag 和 Jscript9 不相符，則傳回 E_JsDEBUG_MISMATCHED_RUNTIME。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebug 介面](../../winscript/reference/ijsdebug-interface.md)