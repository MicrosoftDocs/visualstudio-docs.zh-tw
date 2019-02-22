---
title: IDebugAsyncOperation::GetResult |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d86e9eb2b934bc6bd4027405d06960cd107f81c1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087473"
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