---
title: IDebugSyncOperation：： InProgressAbort |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40974c738c071e52648297ac90a0ab89d9681435
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576673"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
取消在另一個執行緒上進行的作業。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法不接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|無法取消作業。|  
|`E_ABORT`|無法完成作業。|  
  
## <a name="remarks"></a>備註  
 進程 Debug Manager 會從偵錯工具執行緒中呼叫這個方法，以取消正在另一個執行緒中進行的作業。  
  
 如果 `InProgressAbort` 方法無法完成作業，它會儘快傳回 `E_ABORT`。 如果無法取消作業，這個方法就會傳回 `E_NOTIMPL`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugSyncOperation 介面](../../winscript/reference/idebugsyncoperation-interface.md)