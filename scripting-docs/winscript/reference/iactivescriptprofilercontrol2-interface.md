---
title: IActiveScriptProfilerControl2 介面 |Microsoft Docs
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
ms.openlocfilehash: 7059868ae65c5093b24f342bd303ec70172171c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571527"
---
# <a name="iactivescriptprofilercontrol2-interface"></a>IActiveScriptProfilerControl2 介面
提供的方法可讓您在執行腳本時，加入啟動或停止分析的功能。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|通知分析工具您已開始對所有適用的腳本引擎進行程式碼剖析。 這可讓您在開始分析時，取得完整的呼叫堆疊（如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 正在執行）。|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|通知分析工具您即將停止所有適用的腳本引擎上的程式碼剖析。 這可讓您在停止分析時，取得完整的呼叫堆疊（如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 正在執行）。|  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptProfilerControl 介面](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [動態指令碼分析工具介面](../../winscript/reference/active-script-profiler-interfaces.md)