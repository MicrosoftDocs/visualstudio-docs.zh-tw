---
title: 'Ijsdebugframe:: Getdocumentpositionwithid 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4c37f31ca6b75ca826dbdab93847a1e70ff054c1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090008"
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>IJsDebugFrame::GetDocumentPositionWithId 方法
傳回此堆疊框架，在使用者層級文件中的目前位置。  
  
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
 [out]來源文件 （IDebugDocumentText 的指標） 的唯一識別碼。  
  
 `pCharacterOffset`  
 [out]從指令碼開頭以零為起始的字元位移。  
  
 `pStatementCharCount`  
 [out]開始的目前陳述式的長度 * pCharacterOffset，以字元為單位。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)