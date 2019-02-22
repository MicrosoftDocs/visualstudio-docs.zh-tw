---
title: IDebugSyncOperation::Execute |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d8c10973bddef45321b9942afef05a696010433f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090216"
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