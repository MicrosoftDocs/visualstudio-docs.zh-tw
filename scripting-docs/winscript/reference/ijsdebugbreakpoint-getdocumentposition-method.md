---
title: IJsDebugBreakPoint：： GetDocumentPosition 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.GetDocumentPosition
apilocation:
- jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f3bc5aff0b7079e20e2bcd49189153d2ec20d9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577700"
---
# <a name="ijsdebugbreakpointgetdocumentposition-method"></a>IJsDebugBreakPoint::GetDocumentPosition 方法
傳回系結中斷點之語句的位置。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDocumentPosition(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pDocumentId`  
 脫銷來源文件的唯一識別碼（IDebugDocumentText 的指標）。  
  
 `pCharacterOffset`  
 脫銷從腳本開頭以零為起始的字元位移。  
  
 `pStatementCharCount`  
 脫銷目前語句的長度，以字元為開頭，從 * pCharacterOffset 開始。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IJsDebugBreakPoint 介面](../../winscript/reference/ijsdebugbreakpoint-interface.md)