---
title: "IDebugHelper::CreateSimpleConnectionPoint |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugHelper.CreateSimpleConnectionPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreateSimpleConnectionPoint
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fcc598fa97d47a564ddb12aaa0480e42b6601118
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebughelpercreatesimpleconnectionpoint"></a>IDebugHelper::CreateSimpleConnectionPoint
傳回包裝的事件介面指定`IDispatch`物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp  
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdisp`  
 [in]`IDispatch`包裝的物件。  
  
 `ppscp`  
 [out]事件介面包裝`pdisp`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 傳回包裝的事件介面指定`IDispatch`(請參閱[ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md))。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugHelper 介面](../../winscript/reference/idebughelper-interface.md)   
 [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)