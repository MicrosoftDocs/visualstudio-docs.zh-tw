---
title: "IPerPropertyBrowsing2::GetPredefinedStrings |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IPerPropertyBrowsing2.GetPredefinedStrings
apilocation: scrobj.dll
helpviewer_keywords: IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e07d52eca9434acc7e54f3b35b111cf12af0a871
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
可讓呼叫者，使用計數的陣列，代表這個屬性的可能值的字串指標的填滿清單方塊。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dispid`  
 [in]屬性為其呼叫端要求的字串清單的分派識別項。  
  
 `pCaStrings`  
 [out]呼叫端配置計數的陣列結構，其中包含的項目計數和方法配置之陣列的字串指標的位址指標。 如果方法失敗，會配置任何記憶體，且結構的內容是未定義。  
  
 `pCaCookies`  
 [out]結構指標，呼叫端配置計數的陣列，其中包含項目計數和 Dword 方法配置陣列的位址。 如果方法失敗，會配置任何記憶體，且結構的內容是未定義。  
  
## <a name="return-value"></a>傳回值  
 傳回有效`HRESULT`，通常`S_OK`。  
  
## <a name="see-also"></a>另請參閱  
 [IPerPropertyBrowsing2 介面 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)