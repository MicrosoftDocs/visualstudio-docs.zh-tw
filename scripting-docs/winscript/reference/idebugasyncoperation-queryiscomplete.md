---
title: IDebugAsyncOperation：： QueryIsComplete |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.QueryIsComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::QueryIsComplete
ms.assetid: fcf6e229-4d40-46d9-ab81-d3561bc8e084
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51bbfa6a19a247f378a0408e250651c94219fcb5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573256"
---
# <a name="idebugasyncoperationqueryiscomplete"></a>IDebugAsyncOperation::QueryIsComplete
判斷 debug 作業是否已完成。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法不接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|作業已完成。|  
|`S_FALSE`|作業未完成。|  
  
## <a name="remarks"></a>備註  
 這個方法會判斷 debug 作業是否已完成。  
  
## <a name="see-also"></a>請參閱  
 [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)