---
title: IDebugApplicationNodeEvents::onAttach |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAttach
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAttach
ms.assetid: b610c7e4-1c96-47ee-958e-3a1f5f621af3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85147e667f4e83698e23792a43020641974482a6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091256"
---
# <a name="idebugapplicationnodeeventsonattach"></a>IDebugApplicationNodeEvents::onAttach
處理表示偵錯應用程式節點物件已附加至父節點的事件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT onAttach(  
   IDebugApplicationNode*  prddpParent  
);  
```  
  
#### <a name="parameters"></a>參數  
 `prddpParent`  
 [in]偵錯應用程式節點，此節點的父系。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會處理表示偵錯應用程式節點物件已附加至父節點的事件。  
  
 實作器`IDebugApplicationNode`介面會引發這個事件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationNodeEvents 介面](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)   
 [IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)