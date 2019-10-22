---
title: IJsDebugFrame：：評估方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 6227b97c1fd5fae32db3e13ef72751726c36b043
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573490"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate 方法
評估此堆疊框架內容中的運算式。  
  
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
 在要評估的運算式。  
  
 `ppDebugProperty`  
 脫銷代表屬性瀏覽器的物件。  
  
 `pError`  
 脫銷錯誤訊息（如果發生錯誤）。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 傳回下列內容： S_OK：評估成功，* ppDebugProperty 包含評估結果。 S_FALSE：評估會擲回錯誤（或不支援評估作業），\*pError 包含錯誤訊息。  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)