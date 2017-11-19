---
title: "IDebugApplicationNodeEvents 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20d0fac68bb7cdb3d7f5cb6aac6b0ab67e373c84
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeevents-interface"></a>IDebugApplicationNodeEvents 介面
提供的事件介面`IDebugApplicationNode`介面。  
  
 除了繼承自`IUnknown`、`IDebugApplicationNodeEvents`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|處理事件的子節點加入至偵錯應用程式節點物件時。|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|處理事件的子節點從 偵錯應用程式節點物件中移除時。|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|處理表示偵錯應用程式節點物件已卸離，從父節點的事件。|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|處理表示偵錯應用程式節點物件已附加至父節點的事件。|  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)