---
title: 'Ijsenumdebugproperty:: Next 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsEnumDebugProperty.Next
apilocation:
- jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e6b0e3499f9420d42660880f616d2d0873d7a0f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086771"
---
# <a name="ijsenumdebugpropertynext-method"></a>IJsEnumDebugProperty::Next 方法
會讀取這個物件的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### <a name="parameters"></a>參數  
 `count`  
 [in]要讀取的屬性數目。  
  
 `ppDebugProperty`  
 [out]物件，代表屬性瀏覽器。  
  
 `pActualCount`  
 [out]實際物件的屬性數目。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsEnumDebugProperty 介面](../../winscript/reference/ijsenumdebugproperty-interface.md)