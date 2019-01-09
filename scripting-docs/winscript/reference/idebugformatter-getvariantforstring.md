---
title: IDebugFormatter::GetVariantForString |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetVariantForString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetVariantForString
ms.assetid: 2993431d-0ee2-4d8d-b62c-0a810a8bc391
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ee40057043751b465c6575575f00dee848a0160
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086615"
---
# <a name="idebugformattergetvariantforstring"></a>IDebugFormatter::GetVariantForString
傳回包含指定的字串的 VARIANT。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pwstrValue`  
 [in]若要在變數中儲存的字串。  
  
 `pvar`  
 [out]VARIANT 包含`pwstrValue`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回包含指定的字串的 VARIANT。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugFormatter 介面](../../winscript/reference/idebugformatter-interface.md)