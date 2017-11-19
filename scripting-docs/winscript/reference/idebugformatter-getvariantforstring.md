---
title: "IDebugFormatter::GetVariantForString |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugFormatter.GetVariantForString
apilocation: jscript.dll
helpviewer_keywords: IDebugFormatter::GetVariantForString
ms.assetid: 2993431d-0ee2-4d8d-b62c-0a810a8bc391
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f9f783c8fe1864999e017ff348853df5464c93f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugformattergetvariantforstring"></a>IDebugFormatter::GetVariantForString
傳回包含指定的字串的 VARIANT。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pwstrValue`  
 [in]在變數中儲存的字串。  
  
 `pvar`  
 [out]VARIANT 包含`pwstrValue`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回包含指定的字串的 VARIANT。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugFormatter 介面](../../winscript/reference/idebugformatter-interface.md)