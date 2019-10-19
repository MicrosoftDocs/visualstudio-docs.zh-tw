---
title: IJsDebugFrame：： GetDocumentPositionWithId 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithId
apilocation:
- jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f35f6fb84db95950fe83d571c9f5e5e7db9de1e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573865"
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>IJsDebugFrame::GetDocumentPositionWithId 方法
傳回此堆疊框架在使用者層級檔中的目前位置。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDocumentPositionWithId(  
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
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)