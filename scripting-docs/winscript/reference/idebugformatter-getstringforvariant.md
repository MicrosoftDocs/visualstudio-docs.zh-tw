---
title: IDebugFormatter：： GetStringForVariant |Microsoft Docs
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
ms.openlocfilehash: 5f703396190f1fb7791306ee9e389b676e749f8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576374"
---
# <a name="idebugformattergetstringforvariant"></a>IDebugFormatter::GetStringForVariant
傳回表示指定之 VARIANT 值的字串。  
  
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
 在表示為字串的 VARIANT。  
  
 `nRadix`  
 在用於數值的基數。  
  
 `pbstrValue`  
 脫銷表示 `pvar` 的字串。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回代表指定之 variant 值的字串。  
  
## <a name="see-also"></a>請參閱  
 [IDebugFormatter 介面](../../winscript/reference/idebugformatter-interface.md)