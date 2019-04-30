---
title: IDebugAsyncOperation::GetResult | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetResult
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49cf761c85fce3f8fc2f6705d114ab042e0c2ecd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822041"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
提供同步偵錯作業傳回的物件參數與傳回值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `phrResult`  
 [out]如果作業完成時，`phrResult`的傳回值`IDebugSyncOperation::Execute`。  
  
 `ppunkResult`  
 [out]如果作業已完成，`ppunkResult`是作業所傳回的物件參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_PENDING`|作業尚未完成。|  
  
## <a name="remarks"></a>備註  
 如果在作業完成，則這個方法會傳回`HRESULT`物件參數和`IDebugSyncOperation::Execute`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)