---
title: "IActiveScriptProfilerControl5 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7fd0ce34-6ae3-428f-ba90-3e86a8a98ed0
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0c8b464004337b41280d6d19821f0fb9f1f50a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol5-interface"></a>IActiveScriptProfilerControl5 介面
提供方法來列舉相關聯的指令碼引擎的 GC 堆積物件。  
  
## <a name="syntax"></a>語法  
  
```  
interface IActiveScriptProfilerControl5 : IActiveScriptProfilerControl4  
```  
  
## <a name="methods"></a>方法  
 [IActiveScriptProfilerControl5::EnumHeap2 方法](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)  
 傳回的介面 ([IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md))，可用來逐一查看 GC 堆積中物件的內容相關聯的指令碼引擎。