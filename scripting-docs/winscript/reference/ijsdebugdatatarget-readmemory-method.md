---
title: "Ijsdebugdatatarget:: Readmemory 方法 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.ReadMemory
apilocation: jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc1b67b33e17761a675d6ced9e175b4206ede2e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory 方法
讀取目標處理序的記憶體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>參數  
 `address`  
 [in]要從其中讀取目標處理序的記憶體基底位址。  
  
 `flags`  
 [in]控制行為的 ReadMemory 旗標。  
  
 `pBuffer`  
 [out]從目標處理序的位址空間接收內容的緩衝區。 如果失敗，這個緩衝區的內容會是 unspecified。  
  
 `size`  
 [in]要從程序中讀取的位元組數目。  
  
 `pBytesRead`  
 [out]指出從目標處理序所讀取的位元組數目。 如果 JsDebugAllowPartialRead 已取消選取，這個值一律會成功是完全等於輸入的大小。 如果指定 JsDebugAllowPartialRead，成功時，這個值會是小於或等於零。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 傳回 S_OK 上成功與失敗碼適用於任何錯誤。 如果位址不正確，請傳回 E_JsDEBUG_INVALID_MEMORY_ADDRESS。 如需詳細資訊，請參閱 JsDebugAllowPartialRead。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)