---
title: IActiveScriptProfilerControl3 介面 |Microsoft 文件
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
ms.openlocfilehash: eed00579acfb09217183a1dd1d858a1e99257a2c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724448"
---
# <a name="iactivescriptprofilercontrol3-interface"></a>IActiveScriptProfilerControl3 介面
提供方法來列舉相關聯的指令碼引擎的 GC 堆積物件。  
  
## <a name="syntax"></a>語法  
  
```  
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## <a name="methods"></a>方法  
 [IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 傳回的介面 ([IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md))，可用來逐一查看 GC 堆積中物件的內容相關聯的指令碼引擎。