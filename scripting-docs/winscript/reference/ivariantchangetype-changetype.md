---
title: IVariantChangeType：： ChangeType |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 406d5d8486b3016f0105b7bd8bf231db0e1e9613
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571777"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
採用 variant 值，並使用指定的型別建立新的 variant。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pvarDst`  
 [in、out]Variant，包含 `pvarSrc` 所表示的值，但具有 `vtNew` 所指定的類型。  
  
 `pvarSrc`  
 在要變更為新類型的變數值。  
  
 `lcid`  
 在將引數轉換為或從字串轉換成時要使用的地區設定內容。  
  
 `vtNew`  
 在指定要成為 `pvarDst` 的類型。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 @No__t_0 和 `pvarSrc` 引數可能相等，在此情況下會覆寫原始值。 這個方法會將 `pvarDst` 傳遞給 `VariantClear` 函數，因此 `pvarDst` 應該初始化為有效的值。  
  
## <a name="see-also"></a>請參閱  
 [IVariantChangeType 介面](../../winscript/reference/ivariantchangetype-interface.md)