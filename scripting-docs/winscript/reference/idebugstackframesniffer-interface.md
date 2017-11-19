---
title: "IDebugStackFrameSniffer 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 250c104d24f27900a6ff0eb8e8f72644f820bf5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesniffer-interface"></a>IDebugStackFrameSniffer 介面
可用來列舉元件的已知的邏輯的堆疊框架。 指令碼引擎通常會實作這個介面。 此介面來尋找所有堆疊框架的處理序偵錯管理員使用相關聯之給定執行緒。  
  
> [!NOTE]
>  偵錯工具會呼叫這個介面從感興趣的執行緒內。 指令碼引擎必須識別目前的執行緒，並傳回適當的列舉值。  
  
## <a name="methods"></a>方法  
 除了繼承自`IUnknown`、`IDebugStackFrameSniffer`介面會公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|傳回目前執行緒的堆疊框架的列舉值。|