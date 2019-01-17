---
title: IActiveScriptProfilerControl2 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2 interface
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dad5d4a90eecdc6c93d86df9f9b18273bc471a4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349760"
---
# <a name="iactivescriptprofilercontrol2-interface"></a>IActiveScriptProfilerControl2 介面
提供新增的功能，來啟動或停止執行指令碼時，程式碼剖析的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|通知分析工具，您已開始分析在所有適用的指令碼引擎。 這可讓您取得的完整呼叫堆疊，如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]啟動程式碼剖析時執行。|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|您要停止分析在所有適用的指令碼引擎通知分析工具。 這可讓您取得的完整呼叫堆疊，如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]停止程式碼剖析時執行。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerControl 介面](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [動態指令碼分析工具介面](../../winscript/reference/active-script-profiler-interfaces.md)