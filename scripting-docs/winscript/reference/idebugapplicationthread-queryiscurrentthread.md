---
title: IDebugApplicationThread::QueryIsCurrentThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.QueryIsCurrentThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::QueryIsCurrentThread
ms.assetid: 1580d3aa-3be8-4779-ac7b-41ab5c9edede
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d8871d197d662d179fa4d1ed8d420c48ecc5ab3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154763"
---
# <a name="idebugapplicationthreadqueryiscurrentthread"></a>IDebugApplicationThread::QueryIsCurrentThread
判斷這個執行緒是否為目前執行的執行緒。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT QueryIsCurrentThread();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|此方法成功，這是目前執行的執行緒。|  
|`S_FALSE`|這不是目前執行的執行緒。|  
  
## <a name="remarks"></a>備註  
 這個方法會判斷是否這個執行緒是目前執行的執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationThread 介面](../../winscript/reference/idebugapplicationthread-interface.md)