---
title: IDebugFormatter：： GetStringForVarType |Microsoft Docs
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
ms.openlocfilehash: b9b498f5b37a9fc34b0926d9c0a5601d89dde7c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576352"
---
# <a name="idebugformattergetstringforvartype"></a>IDebugFormatter::GetStringForVarType
傳回表示指定的 VARTYPE 值的字串。  
  
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
 在以 VARTYPE 表示為字串。  
  
 `ptdescArrayType`  
 在描述類型的結構陣列。  
  
 `pbstr`  
 脫銷表示 `vt` 的字串。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 方法會傳回代表指定的 VARTYPE 值的字串。  
  
## <a name="see-also"></a>請參閱  
 [IDebugFormatter 介面](../../winscript/reference/idebugformatter-interface.md)