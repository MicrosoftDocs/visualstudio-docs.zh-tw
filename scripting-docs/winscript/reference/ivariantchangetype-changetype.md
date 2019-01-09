---
title: IVariantChangeType::ChangeType |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0a02b8a3991ff6d20370cd4a2ea4cd87aa9a1226
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086576"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
採用 variant 值，並建立新的變數與指定的型別。  
  
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
 [in、 out]包含所表示之值的 variant `pvarSrc`，但所指定之類型`vtNew`。  
  
 `pvarSrc`  
 [in]Variant 值，以變更至新的型別。  
  
 `lcid`  
 [in]要轉換的引數，或從字串時使用的地區設定內容。  
  
 `vtNew`  
 [in]指定的型別`pvarDst`變成。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 `pvarDst`和`pvarSrc`引數可能是相等的在此情況下會覆寫原始的值。 此方法會傳遞`pvarDst`要`VariantClear`函式，並進而`pvarDst`應該初始化為一個有效的值。  
  
## <a name="see-also"></a>另請參閱  
 [IVariantChangeType 介面](../../winscript/reference/ivariantchangetype-interface.md)