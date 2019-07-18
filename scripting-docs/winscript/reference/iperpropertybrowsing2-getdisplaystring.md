---
title: IPerPropertyBrowsing2::GetDisplayString |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetDisplayString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetDisplayString
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6f63db8d9c032b8e880f05d4d21e50fd56c74e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944877"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
取得顯示類型不是原本就可檢視傳回的文字的字串會描述屬性的名稱，並且可以在呼叫者的使用者介面中顯示。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dispid`  
 [in]分派識別項，其顯示名稱要求的屬性。  
  
 `pBstr`  
 [out]指標`BSTR`包含所識別之屬性的顯示名稱`dispID`。  
  
## <a name="return-value"></a>傳回值  
 會傳回有效`HRESULT`，通常是`S_OK`。  
  
## <a name="remarks"></a>備註  
 傳回的字串不是屬性合法值。 它是只顯示一個字串的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [IPerPropertyBrowsing2 介面 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)