---
title: "使用中指令碼的常數、 列舉和錯誤碼 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb4165a5471c8e79827f0f7605cef575e82bab75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>動態指令碼的常數、列舉和錯誤碼
本節描述在 Windows 指令碼引擎所使用的錯誤碼與列舉型別。  
  
## <a name="constants"></a>常數  
  
|常數|說明|  
|--------------|-----------------|  
|[SCRIPTTHREADID 常數](../../winscript/reference/scriptthreadid-constants.md)|指定執行緒的類型。|  
  
## <a name="properties"></a>屬性  
  
|屬性|說明|  
|--------------|-----------------|  
|[SCRIPTPROP_HOSTKEEPALIVE 屬性](../../winscript/reference/scriptprop-hostkeepalive-property.md)|用來指定應該保存的指令碼引擎完整運作，如果有未處理的參考。|  
  
## <a name="enumerations"></a>列舉  
  
|列舉|說明|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE 列舉](../../winscript/reference/scriptgctype-enumeration.md)|若要執行記憶體回收的類型。|  
|[SCRIPTLANGUAGEVERSION 列舉](../../winscript/reference/scriptlanguageversion-enumeration.md)|指定可能的指令碼版本。|  
|[SCRIPTSTATE 列舉](../../winscript/reference/scriptstate-enumeration.md)|指定指令碼引擎的狀態。|  
|||  
|[SCRIPTTHREADSTATE 列舉](../../winscript/reference/scriptthreadstate-enumeration.md)|指定在指令碼引擎的執行緒的狀態。|  
|[SCRIPTTRACEINFO 列舉](../../winscript/reference/scripttraceinfo-enumeration.md)|表示所追蹤的指令碼事件。 用於[iactivescriptsitetraceinfo:: Sendscripttraceinfo 方法](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)。|  
|[SCRIPTUICHANDLING 列舉](../../winscript/reference/scriptuichandling-enumeration.md)|表示應該處理 UI 控制項的方式。|  
|[SCRIPTUICITEM 列舉](../../winscript/reference/scriptuicitem-enumeration.md)|代表 UI 項目類型。 用於[iactivescriptsiteuicontrol:: Getuibehavior 方法](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md)。|  
  
## <a name="error-codes"></a>錯誤碼  
  
|錯誤碼|說明|  
|----------------|-----------------|  
|[SCRIPT_E_PROPAGATE 錯誤碼](../../winscript/reference/script-e-propagate-error-code.md)|指令碼錯誤傳播至呼叫端，這可能是在不同的執行緒。|  
|[SCRIPT_E_RECORDED 錯誤碼](../../winscript/reference/script-e-recorded-error-code.md)|已將指令碼引擎與主機之間傳遞錯誤。|  
|[SCRIPT_E_REPORTED 錯誤碼](../../winscript/reference/script-e-reported-error-code.md)|指令碼引擎回報給主機處理的例外狀況。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼介面](../../winscript/reference/active-script-interfaces.md)