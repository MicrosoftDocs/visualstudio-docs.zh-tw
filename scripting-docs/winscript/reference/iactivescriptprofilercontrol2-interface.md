---
title: IActiveScriptProfilerControl2 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 11987054ed934f4004333f136ea35696ff6c394f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147003"
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