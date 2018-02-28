---
title: "IDebugApplication::CreateAsyncDebugOperation |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.CreateAsyncDebugOperation
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::CreateAsyncDebugOperation
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8714f4401249d73cf09d241ebf4c2b2115911d6b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
提供非同步存取指定的同步偵錯作業。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>參數  
 `psdo`  
 [in]同步的偵錯作業物件中。  
  
 `ppado`  
 [out]非同步偵錯作業物件中。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法可讓語言引擎來以非同步方式評估運算式，而不明確地同步處理與偵錯工具執行緒。 如需詳細資訊，請參閱[IDebugSyncOperation 介面](../../winscript/reference/idebugsyncoperation-interface.md)和[IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugSyncOperation 介面](../../winscript/reference/idebugsyncoperation-interface.md)   
 [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)