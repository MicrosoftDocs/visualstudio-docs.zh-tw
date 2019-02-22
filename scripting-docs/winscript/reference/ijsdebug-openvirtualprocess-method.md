---
title: 'Ijsdebug:: Openvirtualprocess 方法 |Microsoft Docs'
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
ms.openlocfilehash: daa5414153ee55a431294afaf7b167ee91839bfc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093986"
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