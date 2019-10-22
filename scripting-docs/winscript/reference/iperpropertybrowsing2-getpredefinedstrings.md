---
title: IPerPropertyBrowsing2：： GetPredefinedStrings |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55ade724dd9ee5d59feb9d04c5b525ca839a9cec
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576766"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
允許呼叫者填入清單方塊，其中包含代表此屬性可能值的字串指標的計數陣列。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dispid`  
 在呼叫端要求字串清單之屬性的分派識別碼。  
  
 `pCaStrings`  
 脫銷呼叫端配置之計數陣列結構的指標，其中包含方法配置的字串指標陣列的元素計數和位址。 如果方法失敗，則不會配置任何記憶體，而且不會定義結構的內容。  
  
 `pCaCookies`  
 脫銷呼叫端配置的計數陣列結構的指標，其中包含方法配置的 Dword 陣列的元素計數和位址。 如果方法失敗，則不會配置任何記憶體，而且不會定義結構的內容。  
  
## <a name="return-value"></a>傳回值  
 傳回有效的 `HRESULT`，通常是 `S_OK`。  
  
## <a name="see-also"></a>請參閱  
 [IPerPropertyBrowsing2 介面 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)