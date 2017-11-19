---
title: "IDebugAsyncOperation::QueryIsComplete |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugAsyncOperation.QueryIsComplete
apilocation: pdm.dll
helpviewer_keywords: IDebugAsyncOperation::QueryIsComplete
ms.assetid: fcf6e229-4d40-46d9-ab81-d3561bc8e084
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e985697e425ec4966f2260792a9698fa50b4c98d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationqueryiscomplete"></a>IDebugAsyncOperation::QueryIsComplete
判定偵錯作業已完成。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會採用任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|作業已完成。|  
|`S_FALSE`|無法完成作業。|  
  
## <a name="remarks"></a>備註  
 這個方法會判斷是否已完成偵錯作業。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)