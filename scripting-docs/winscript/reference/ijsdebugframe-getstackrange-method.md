---
title: 'Ijsdebugframe:: Getstackrange 方法 |Microsoft 文件'
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
ms.openlocfilehash: cce4d4542f4f76657475636ad6d8e430e1909181
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727868"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange 方法
傳回邏輯 JavaScript 堆疊框架的絕對位址範圍。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pStart`  
 [out]下方大部分的框架的堆疊指標。  
  
 `pEnd`  
 [out]排名最前面的畫面格的大部分堆疊器指標。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 這個方法可用於拼湊交錯的堆疊追蹤所蒐集的多個執行階段。 開始時，結束堆疊指標可以包含多個實體機器堆疊框架 （適用於解譯的 JavaScript 執行階段框架）。 開始 > 結束隨著堆疊從高到低的位址。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)