---
title: "IDebugExpression 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39e139e09362fc392d1110e26837c52fd4c642c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpression-interface"></a>IDebugExpression 介面
表示以非同步方式評估的運算式。 指令碼引擎通常會實作這個介面。 偵錯工具 IDE 通常會使用此介面來啟用立即執行 視窗或監看式視窗。  
  
> [!NOTE]
>  `IDebugExpression`介面就只能從堆疊框架。  
  
 除了繼承自`IUnknown`、`IDebugExpression`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|開始評估的運算式。|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|中止的運算式。|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|判斷作業是否完成。|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|傳回運算式評估為字串和作業的傳回值的結果。|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|傳回做為偵錯屬性和作業的傳回值的運算式評估的結果。|