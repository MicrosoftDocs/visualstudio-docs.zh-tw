---
title: 'Ijsdebugbreakpoint:: Getdocumentposition 方法 |Microsoft Docs'
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
ms.openlocfilehash: 146eb26c887cd24d1eb7af858535fcecac62b41d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583141"
---
# <a name="ijsdebugbreakpointgetdocumentposition-method"></a>IJsDebugBreakPoint::GetDocumentPosition 方法
傳回陳述式的中斷點已繫結的位置。  
  
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
 [out]來源文件 （IDebugDocumentText 的指標） 的唯一識別碼。  
  
 `pCharacterOffset`  
 [out]從指令碼開頭以零為起始的字元位移。  
  
 `pStatementCharCount`  
 [out]開始的目前陳述式的長度 * pCharacterOffset，以字元為單位。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugBreakPoint 介面](../../winscript/reference/ijsdebugbreakpoint-interface.md)