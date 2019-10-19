---
title: IDebugApplicationNodeEvents：： onAttach |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e45af6b931dad28a41f8f4453db9fab96405df3b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574695"
---
# <a name="idebugapplicationnodeeventsonattach"></a>IDebugApplicationNodeEvents::onAttach
處理事件，表示 debug 應用程式節點物件已附加至父節點。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT onAttach(  
   IDebugApplicationNode*  prddpParent  
);  
```  
  
#### <a name="parameters"></a>參數  
 `prddpParent`  
 在屬於此節點之父系的 debug 應用程式節點。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會處理事件，表示 debug 應用程式節點物件已附加至父節點。  
  
 @No__t_0 介面的實施者會引發此事件。  
  
## <a name="see-also"></a>請參閱  
 [IDebugApplicationNodeEvents 介面](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents：： onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)    
 [IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)