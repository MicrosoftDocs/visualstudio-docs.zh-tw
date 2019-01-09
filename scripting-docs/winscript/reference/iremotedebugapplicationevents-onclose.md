---
title: IRemoteDebugApplicationEvents::OnClose |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnClose
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnClose
ms.assetid: 57ef69e0-1ced-480a-a1bf-c91d8d5dd2d2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ad44e0db3c125239b7f877bc856edd0e861d51a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095533"
---
# <a name="iremotedebugapplicationeventsonclose"></a>IRemoteDebugApplicationEvents::OnClose
處理應用程式關閉事件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnClose();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會處理應用程式關閉事件。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplicationEvents 介面](../../winscript/reference/iremotedebugapplicationevents-interface.md)