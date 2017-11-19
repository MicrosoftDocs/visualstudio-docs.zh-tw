---
title: "IRemoteDebugApplicationThread::GetApplication |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationThread.GetApplication
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplicationThread::GetApplication
ms.assetid: 9446c7f9-cfa2-408f-98c5-64f549783de1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15f503f98492606424752dff169fd4b61b6cc8b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationthreadgetapplication"></a>IRemoteDebugApplicationThread::GetApplication
傳回這個執行緒相關聯的應用程式物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetApplication(  
   IRemoteDebugApplication**  pprda  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pprda`  
 [out]這個執行緒相關聯的應用程式物件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回與這個執行緒相關聯的應用程式物件。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplicationThread 介面](../../winscript/reference/iremotedebugapplicationthread-interface.md)