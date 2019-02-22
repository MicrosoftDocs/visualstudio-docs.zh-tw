---
title: IMachineDebugManagerEvents Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9aab3d7abeecd22e830c68f174896df0e7df2da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344020"
---
# <a name="imachinedebugmanagerevents-interface"></a>IMachineDebugManagerEvents 介面
通知機器偵錯管理員所維護的執行中應用程式清單變更。 偵錯工具 IDE 可以使用此介面，顯示應用程式的動態清單。  
  
 除了繼承自方法`IUnknown`，則`IMachineDebugManagerEvents`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|應用程式會加入為 「 正在執行時處理事件的應用程式清單。|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|移除應用程式執行時處理事件的應用程式清單。|