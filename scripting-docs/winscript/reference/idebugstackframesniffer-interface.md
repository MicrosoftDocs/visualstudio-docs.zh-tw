---
title: IDebugStackFrameSniffer 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41fff384bc9075d94fcfa84d94350fec72ebc64a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348876"
---
# <a name="idebugstackframesniffer-interface"></a>IDebugStackFrameSniffer 介面
提供方法來列舉邏輯堆疊框架已知的元件。 指令碼引擎通常會實作這個介面。 此介面來尋找所有堆疊框架的處理序偵錯管理員使用相關聯之給定執行緒。  
  
> [!NOTE]
>  偵錯工具會呼叫此介面內感興趣的執行緒。 指令碼引擎必須找出目前的執行緒，並傳回適當的列舉值。  
  
## <a name="methods"></a>方法  
 除了繼承自方法`IUnknown`，則`IDebugStackFrameSniffer`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|傳回目前執行緒的堆疊框架的列舉值。|