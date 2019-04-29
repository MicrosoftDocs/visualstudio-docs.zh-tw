---
title: IDebugSyncOperation::Execute | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.Execute
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2bc204169ff94a240e363eb8caa35ec8c7de9be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004872"
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
以同步方式執行此作業，並傳回。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppunkResult`  
 [out]作業所傳回的物件參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_ABORT`|作業已中止，藉由呼叫`IDebugSyncOperation::InProgressAbort`方法。|  
  
## <a name="remarks"></a>備註  
 目標執行緒呼叫中的程序進行偵錯管理員`Execute`方法以同步方式。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugSyncOperation 介面](../../winscript/reference/idebugsyncoperation-interface.md)