---
title: "IEnumDebugStackFrames 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IEnumDebugStackFrames interface
ms.assetid: 13484429-0140-4f4f-8502-3ca2a0553ed4
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0174839a25695e9594b4cbbf4db6a302f5a2446
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugstackframes-interface"></a>IEnumDebugStackFrames 介面
列舉對應至執行緒的堆疊框架。  
  
## <a name="methods"></a>方法  
 除了繼承自`IUnknown`、`IEnumDebugStackFrames`介面會公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[IEnumDebugStackFrames::Next](../../winscript/reference/ienumdebugstackframes-next.md)|擷取指定的列舉順序中的區段數目。|  
|[IEnumDebugStackFrames::Skip](../../winscript/reference/ienumdebugstackframes-skip.md)|略過指定的數目的列舉順序中的區段。|  
|[IEnumDebugStackFrames::Reset](../../winscript/reference/ienumdebugstackframes-reset.md)|列舉序列重設為開頭。|  
|[IEnumDebugStackFrames::Clone](../../winscript/reference/ienumdebugstackframes-clone.md)|建立列舉值，包含目前的列舉值的狀態相同。|