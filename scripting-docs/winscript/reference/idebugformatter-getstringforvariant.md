---
title: IDebugFormatter::GetStringForVariant |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetStringForVariant
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetStringForVariant
ms.assetid: 95189d03-1126-433e-8513-659107b3df16
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 901bf9648d4d16faf7386b528cc3fd877070a5b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996851"
---
# <a name="idebugformattergetstringforvariant"></a>IDebugFormatter::GetStringForVariant
傳回字串，表示指定的變數值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pvar`  
 [in]若要表示為字串的 VARIANT。  
  
 `nRadix`  
 [in]若要使用的數字值的基數。  
  
 `pbstrValue`  
 [out]字串，表示`pvar`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回字串，表示指定的變數值。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugFormatter 介面](../../winscript/reference/idebugformatter-interface.md)