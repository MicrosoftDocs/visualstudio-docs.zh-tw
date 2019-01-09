---
title: IDebugApplication::CreateAsyncDebugOperation |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 30051276b682bdf906db72bc2682e1c5d58c455a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090697"
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
提供指定的同步偵錯作業的非同步存取。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 此方法允許語言引擎來以非同步方式評估運算式，而不明確同步處理與偵錯工具執行緒。 如需詳細資訊，請參閱 < [IDebugSyncOperation 介面](../../winscript/reference/idebugsyncoperation-interface.md)並[IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugSyncOperation 介面](../../winscript/reference/idebugsyncoperation-interface.md)   
 [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)