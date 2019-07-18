---
title: IPerPropertyBrowsing2::MapPropertyToPage |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.MapPropertyToPage
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::MapPropertyToPage
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77270bbe963f281a43a085cb7d15724b7b2ec14e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944838"
---
# <a name="iperpropertybrowsing2mappropertytopage"></a>IPerPropertyBrowsing2::MapPropertyToPage
傳回可以用來編輯這個屬性的屬性頁 CLSID。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dispid`  
 [in]分派識別項相關的屬性。  
  
 `pClsidPropPage`  
 [out]識別與屬性相關聯的屬性頁 CLSID 指標。 如果此方法失敗，*`pClsidPropPage`設定為 CLSID_NULL。  
  
## <a name="return-value"></a>傳回值  
 會傳回有效`HRESULT`，通常是`S_OK`。  
  
## <a name="see-also"></a>另請參閱  
 [IPerPropertyBrowsing2 介面 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)