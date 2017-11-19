---
title: "IDebugStackFrameSnifferEx 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56d6e63c41db274634b2593989800ea0392b93a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesnifferex-interface"></a>IDebugStackFrameSnifferEx 介面
可用來列舉元件的已知的邏輯的堆疊框架。 指令碼引擎通常會實作這個介面。 此介面來尋找所有堆疊框架的處理序偵錯管理員使用相關聯之給定執行緒。  
  
> [!NOTE]
>  感興趣的執行緒中呼叫這個介面。 介面實作必須識別目前的執行緒，並傳回適當的列舉值。  
  
 除了繼承自`IDebugStackFrameSniffer`、`IDebugStackFrameSnifferEx`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|傳回目前執行緒的堆疊框架的列舉值。|