---
title: 'Ijsdebugframe:: Evaluate 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.Evaluate
apilocation:
- jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38e826048e85456ca63e069de67701b1fc3e9f04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727448"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate 方法
評估內容中的運算式，此堆疊框架。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pExpressionText`  
 [in]要評估的運算式。  
  
 `ppDebugProperty`  
 [out]物件，表示屬性瀏覽器。  
  
 `pError`  
 [out]錯誤訊息，如果發生錯誤。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 會傳回下列： S_OK： 評估成功時，* ppDebugProperty 包含評估結果。 S_FALSE： 評估擲回的錯誤 （或不支援評估作業）， \*pError 包含錯誤訊息。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)