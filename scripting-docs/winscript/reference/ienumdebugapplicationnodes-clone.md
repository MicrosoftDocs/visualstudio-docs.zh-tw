---
title: IEnumDebugApplicationNodes：： Clone |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugApplicationNodes.Clone
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumDebugApplicationNodes::Clone
ms.assetid: 7190954d-e2da-4a84-8e37-81d4d27886a8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1d5488f260784450d2b7695972c78a5f9271eed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573072"
---
# <a name="ienumdebugapplicationnodesclone"></a>IEnumDebugApplicationNodes::Clone
建立枚舉器，其中包含與目前列舉值相同的狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Clone(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pperddp`  
 脫銷傳回列舉值之複製的 `IEnumDebugApplicationNodes` 介面。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會建立一個列舉值，其中包含與目前列舉值相同的狀態。  
  
## <a name="see-also"></a>請參閱  
 [IEnumDebugApplicationNodes 介面](../../winscript/reference/ienumdebugapplicationnodes-interface.md)