---
title: 'Ijsdebug:: Openvirtualprocess 方法 |Microsoft Docs'
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
ms.openlocfilehash: 97a055bf1550d74dc6b86d93ffdb9ca406afb43d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151943"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess 方法
用來建立新的虛擬程序物件的 factory 方法。  
  
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
 [in]若要附加偵錯工具的處理序識別碼。  
  
 `runtimeJsBaseAddress`  
 [in]在 JavaScript 執行階段載入目標處理序的基底位址。  
  
 `pDataTarget`  
 [in]偵錯工具提供的介面，用於查詢的程序的狀態。  
  
 `ppProcess`  
 [out]新的偵錯處理程序物件  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 如果 Jscript9diag 和 Jscript9 不相符，則傳回 E_JsDEBUG_MISMATCHED_RUNTIME。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebug 介面](../../winscript/reference/ijsdebug-interface.md)