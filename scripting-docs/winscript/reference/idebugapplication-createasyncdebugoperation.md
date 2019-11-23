---
title: IDebugApplication：： CreateAsyncDebugOperation |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.CreateAsyncDebugOperation
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::CreateAsyncDebugOperation
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1feb8207fb7e7a7faf4427be189c4952139ef32c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575565"
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
提供給定同步 debug 作業的非同步存取。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>參數  
 `psdo`  
 在同步的 debug 工作物件。  
  
 `ppado`  
 脫銷非同步 debug 工作物件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法可讓語言引擎以非同步方式評估運算式，而不需要明確地與偵錯工具執行緒同步處理。 如需詳細資訊，請參閱[IDebugSyncOperation 介面](../../winscript/reference/idebugsyncoperation-interface.md)和[IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugSyncOperation 介面](../../winscript/reference/idebugsyncoperation-interface.md)   
 [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)