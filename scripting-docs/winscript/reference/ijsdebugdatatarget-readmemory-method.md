---
title: 'Ijsdebugdatatarget:: Readmemory 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadMemory
apilocation:
- jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 705fff3bf2d4be78897c18c5a4c61bd74a8c2230
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147757"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory 方法
讀取目標處理序的記憶體。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
 [in]要從其中讀取目標處理序的記憶體的基底位址。  
  
 `flags`  
 [in]控制 ReadMemory 行為的旗標。  
  
 `pBuffer`  
 [out]從目標處理序的位址空間接收內容的緩衝區。 在失敗時，這個緩衝區的內容未指定。  
  
 `size`  
 [in]要從程序讀取的位元組數目。  
  
 `pBytesRead`  
 [out]表示從目標處理序讀取的位元組數目。 如果清除 JsDebugAllowPartialRead，成功時這個值一律會輸入大小完全相等。 如果已指定 JsDebugAllowPartialRead，成功時，這個值會是小於或等於零。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 傳回 S_OK 成功和失敗碼適用於任何錯誤。 如果位址無效，則傳回 E_JsDEBUG_INVALID_MEMORY_ADDRESS。 如需詳細資訊，請參閱 JsDebugAllowPartialRead。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)