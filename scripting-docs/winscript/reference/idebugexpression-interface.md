---
title: IDebugExpression 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 589c231afbc149c4eeface784d3cdbd43c4e5e40
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156342"
---
# <a name="idebugexpression-interface"></a>IDebugExpression 介面
代表非同步評估的運算式。 指令碼引擎通常會實作這個介面。 偵錯工具 IDE 通常會使用此介面來啟用 [立即執行] 視窗或監看式視窗。  
  
> [!NOTE]
>  `IDebugExpression`介面可供使用，只會從堆疊框架。  
  
 除了繼承自方法`IUnknown`，則`IDebugExpression`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|開始評估運算式。|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|中止的運算式。|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|判斷作業是否完成。|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|傳回字串，以及作業的傳回值的運算式評估的結果。|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|傳回做為偵錯屬性和作業的傳回值的運算式評估的結果。|