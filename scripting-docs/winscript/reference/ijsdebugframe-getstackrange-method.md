---
title: 'Ijsdebugframe:: Getstackrange 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 049be8a665dae396d4e92fe847e757b266dc6025
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090281"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange 方法
傳回邏輯 JavaScript 堆疊框架的絕對位址範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pStart`  
 [out]Bottom 圖文框的多數堆疊指標。  
  
 `pEnd`  
 [out]最上層大部分圖文的多數堆疊指標。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 此方法相當實用，對於拼湊從多個執行階段收集的交錯的堆疊追蹤。 開始、 結束堆疊指標可能包含多個實體機器堆疊框架 （解譯的 JavaScript 執行階段架構）。 開始 > 結束隨著堆疊從高位址向低位址。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)