---
title: IDebugFormatter::GetStringForVarType |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetStringForVarType
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetStringForVarType
ms.assetid: 1c1a0499-ca57-47e0-8367-fdb4c902bca3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d83df97ac9cb6c38d989470b71da93aceb5d50b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979210"
---
# <a name="idebugformattergetstringforvartype"></a>IDebugFormatter::GetStringForVarType
傳回字串，表示指定的 VARTYPE 值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetStringForVarType(  
   VARTYPE    vt,  
   TYPEDESC*  ptdescArrayType,  
   BSTR*      pbstr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `vt`  
 [in]若要表示為字串的 VARTYPE。  
  
 `ptdescArrayType`  
 [in]結構描述類型的陣列。  
  
 `pbstr`  
 [out]字串，表示`vt`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 方法會傳回字串，表示指定的 VARTYPE 值。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugFormatter 介面](../../winscript/reference/idebugformatter-interface.md)