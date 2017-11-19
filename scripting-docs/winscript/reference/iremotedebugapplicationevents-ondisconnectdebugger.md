---
title: "IRemoteDebugApplicationEvents::OnDisconnectDebugger |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationEvents.OnDisconnectDebugger
apilocation: jscript.dll
helpviewer_keywords: IRemoteDebugApplicationEvents::OnDisconnectDebugger
ms.assetid: ea11cde0-1484-4181-a5dd-a1f6cf788892
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 014da34fb9f7c6f3841d44a354320ff55bacc316
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationeventsondisconnectdebugger"></a>IRemoteDebugApplicationEvents::OnDisconnectDebugger
偵錯工具的控點中斷連線事件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OnDisconnectDebugger();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會採用任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會處理偵錯工具中斷連線事件。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplicationEvents 介面](../../winscript/reference/iremotedebugapplicationevents-interface.md)