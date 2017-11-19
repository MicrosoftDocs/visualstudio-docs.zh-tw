---
title: "Ijsenumdebugproperty:: Next 方法 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsEnumDebugProperty.Next
apilocation: jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8c85601709bb727549152ffdb01e15dbd84e510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ijsenumdebugpropertynext-method"></a>IJsEnumDebugProperty::Next 方法
讀取此物件屬性。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [out]物件，表示屬性瀏覽器。  
  
 `pActualCount`  
 [out]物件的屬性的實際數目。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsEnumDebugProperty 介面](../../winscript/reference/ijsenumdebugproperty-interface.md)