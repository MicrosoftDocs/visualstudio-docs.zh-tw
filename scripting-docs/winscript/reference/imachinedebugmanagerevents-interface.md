---
title: "IMachineDebugManagerEvents 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 369dc8d182efe7bf9697454d0e4b1c9c1a10c027
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagerevents-interface"></a>IMachineDebugManagerEvents 介面
表示執行中的變更電腦偵錯管理員所維護的應用程式清單。 IDE 偵錯工具可以使用這個介面，顯示應用程式的動態清單。  
  
 除了繼承自`IUnknown`、`IMachineDebugManagerEvents`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|加入應用程式執行時處理事件的應用程式清單。|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|在移除應用程式執行時處理事件的應用程式清單。|