---
title: IPerPropertyBrowsing2::GetPredefinedStrings |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a60225e69a04399a3ff0160291b84e9f3fda513c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915956"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
可讓呼叫者使用的計數的陣列，代表這個屬性的可能值的字串指標的填滿清單方塊。  
  
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
 [in]為其呼叫端要求的字串清單屬性的分派識別項。  
  
 `pCaStrings`  
 [out]呼叫端配置計數的陣列結構，其中包含的項目計數和地址的字串指標的方法配置陣列的指標。 如果方法失敗，會配置任何記憶體，與結構的內容為未定義。  
  
 `pCaCookies`  
 [out]呼叫端配置計數的陣列結構，其中包含的項目計數和 Dword 的方法配置陣列的位址指標。 如果方法失敗，會配置任何記憶體，與結構的內容為未定義。  
  
## <a name="return-value"></a>傳回值  
 會傳回有效`HRESULT`，通常是`S_OK`。  
  
## <a name="see-also"></a>另請參閱  
 [IPerPropertyBrowsing2 介面 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)