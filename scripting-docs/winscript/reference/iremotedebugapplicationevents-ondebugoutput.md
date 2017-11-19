---
title: "IRemoteDebugApplicationEvents::OnDebugOutput |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationEvents.OnDebugOutput
apilocation: jscript.dll
helpviewer_keywords: IRemoteDebugApplicationEvents::OnDebugOutput
ms.assetid: db08872e-3d84-4d7f-bf94-a851bf43a333
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 022a2297e135f308a8250fa0b493dd5943da7687
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationeventsondebugoutput"></a>IRemoteDebugApplicationEvents::OnDebugOutput
處理偵錯工具輸出事件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OnDebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstr`  
 [in]偵錯輸出字串。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會處理偵錯工具輸出事件。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplicationEvents 介面](../../winscript/reference/iremotedebugapplicationevents-interface.md)