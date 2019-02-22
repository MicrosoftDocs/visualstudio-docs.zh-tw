---
title: IActiveScriptProfilerControl3 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 64bc860a-54d4-475a-80f6-2f9dba6448ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bebe351608b3136ac00a059bffab3535141e7fca
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344716"
---
# <a name="iactivescriptprofilercontrol3-interface"></a>IActiveScriptProfilerControl3 介面
提供方法來列舉與指令碼引擎相關聯的 GC 堆積物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## <a name="methods"></a>方法  
 [IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 傳回的介面 ([IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md))，可用來逐一查看 GC 堆積物件相關聯的指令碼引擎的內容中。