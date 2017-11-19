---
title: "IRemoteDebugApplication::GetDebugger |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplication.GetDebugger
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplication::GetDebugger
ms.assetid: 3d173b86-9281-4a3c-9550-d79408fd50ba
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 908d6b43ca33a3b9c35d2690ccb5453032ce151a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationgetdebugger"></a>IRemoteDebugApplication::GetDebugger
傳回目前的偵錯工具連接到應用程式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetDebugger(  
   IApplicationDebugger**  pad  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pad`  
 [out]目前的偵錯工具連接到應用程式。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回目前的偵錯工具連接到應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)   
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)