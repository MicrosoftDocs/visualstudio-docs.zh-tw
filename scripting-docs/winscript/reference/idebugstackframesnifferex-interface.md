---
title: IDebugStackFrameSnifferEx 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dccd9210908922951c20378868c33b3389cbed4f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432243"
---
# <a name="idebugstackframesnifferex-interface"></a>IDebugStackFrameSnifferEx 介面
提供方法來列舉邏輯堆疊框架已知的元件。 指令碼引擎通常會實作這個介面。 此介面來尋找所有堆疊框架的處理序偵錯管理員使用相關聯之給定執行緒。  
  
> [!NOTE]
> 這個介面會從感興趣的執行緒內呼叫。 介面實作必須找出目前的執行緒，並傳回適當的列舉值。  
  
 除了繼承自方法`IDebugStackFrameSniffer`，則`IDebugStackFrameSnifferEx`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|傳回目前執行緒的堆疊框架的列舉值。|