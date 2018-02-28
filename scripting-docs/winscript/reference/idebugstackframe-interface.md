---
title: "IDebugStackFrame 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrame interface
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36fa0ba2d1b4049ad41ff0502ed33be0a706d9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframe-interface"></a>IDebugStackFrame 介面
表示執行緒堆疊上的邏輯的堆疊框架。 呼叫`IDebugStackFrame::QueryInterface`方法，以取得`IDebugExpressionContext`介面，可讓運算式評估] 和 [監看式視窗。  
  
 除了繼承自`IUnknown`、`IDebugStackFrame`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|傳回目前的堆疊框架相關聯的程式碼內容。|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|傳回堆疊框架的短或長時間的文字的描述。|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|傳回的短或長時間的文字描述的語言。|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|傳回此堆疊框架相關聯的執行緒。|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|傳回目前的框架屬性瀏覽器。|