---
title: 'Ijsdebugframe:: Evaluate 方法 |Microsoft Docs'
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
ms.openlocfilehash: 574af7823add67a00fc8add922b5e352fa1b369c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091919"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate 方法
評估此堆疊框架的內容中的運算式。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
 [out]物件，代表屬性瀏覽器。  
  
 `pError`  
 [out]錯誤訊息，如果發生錯誤。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 傳回下列結果：S_OK:評估成功，* ppDebugProperty 包含評估結果。 S_FALSE:評估擲回錯誤 （或不支援評估作業）， \*pError 包含錯誤訊息。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)