---
title: "IDebugApplicationNodeEvents::onAddChild |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationNodeEvents.onAddChild
apilocation: scrobj.dll
helpviewer_keywords: IDebugApplicationNodeEvents::onAddChild
ms.assetid: 59ce33cf-1843-4b03-98a2-34859d3023f7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3df872cd14b6d7fcd455371d1601b2a4082fb39a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeeventsonaddchild"></a>IDebugApplicationNodeEvents::onAddChild
處理事件的子節點加入至偵錯應用程式節點物件時。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT onAddChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>參數  
 `prddpChild`  
 [in]已加入子偵錯應用程式節點。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法時處理事件的子節點加入至偵錯應用程式節點物件。  
  
 實作器`IDebugApplicationNode`介面會引發這個事件  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationNodeEvents 介面](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)   
 [IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)