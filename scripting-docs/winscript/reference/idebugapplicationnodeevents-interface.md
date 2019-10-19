---
title: IDebugApplicationNodeEvents 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2f72290e331a51f1b33746b22a6526c9bfbac7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574723"
---
# <a name="idebugapplicationnodeevents-interface"></a>IDebugApplicationNodeEvents 介面
提供 `IDebugApplicationNode` 介面的事件介面。  
  
 除了繼承自 `IUnknown` 的方法之外，`IDebugApplicationNodeEvents` 介面也會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|當子節點加入至 debug 應用程式節點物件時，處理事件。|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|從 debug 應用程式節點物件中移除子節點時，處理事件。|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|處理事件，表示已從父節點卸離 debug 應用程式節點物件。|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|處理事件，表示 debug 應用程式節點物件已附加至父節點。|  
  
## <a name="see-also"></a>請參閱  
 [IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)