---
title: IEnumDebugStackFrames Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugStackFrames interface
ms.assetid: 13484429-0140-4f4f-8502-3ca2a0553ed4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 224c26bccc5443cb20e2ca514ac6df1a111df05e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963360"
---
# <a name="ienumdebugstackframes-interface"></a>IEnumDebugStackFrames 介面
列舉對應至執行緒的堆疊框架。  
  
## <a name="methods"></a>方法  
 除了繼承自方法`IUnknown`，則`IEnumDebugStackFrames`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IEnumDebugStackFrames::Next](../../winscript/reference/ienumdebugstackframes-next.md)|擷取指定的數目的列舉型別序列中的區段。|  
|[IEnumDebugStackFrames::Skip](../../winscript/reference/ienumdebugstackframes-skip.md)|略過指定的數目的列舉型別序列中的區段。|  
|[IEnumDebugStackFrames::Reset](../../winscript/reference/ienumdebugstackframes-reset.md)|將列舉型別序列重設到開頭。|  
|[IEnumDebugStackFrames::Clone](../../winscript/reference/ienumdebugstackframes-clone.md)|建立列舉值，包含目前的列舉值相同的狀態。|