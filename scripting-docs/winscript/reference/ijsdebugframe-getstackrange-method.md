---
title: IJsDebugFrame：： GetStackRange 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d1ac3cbee9d16296632477f4128ec36370ab0d4a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574046"
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
 脫銷框架的最下方堆疊指標。  
  
 `pEnd`  
 脫銷框架的最上層堆疊指標。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 這個方法適用于將從多個執行時間收集而來的交錯堆疊追蹤 piecing 在一起。 開始、結束堆疊指標可以包含多個實體機器堆疊框架（適用于已解讀的 JavaScript 執行時間框架）。 當堆疊從高到低的位址增加時，啟動 > 結束。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)