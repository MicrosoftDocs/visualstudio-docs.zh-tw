---
title: 作用中的指令碼的常數、 列舉和錯誤碼 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 090b494e904fbef1c0d3d8b380f7a184a6042788
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953994"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>動態指令碼的常數、列舉和錯誤碼
本章節描述列舉和錯誤碼在 Windows 指令碼引擎中使用。  
  
## <a name="constants"></a>常數  
  
|常數|描述|  
|--------------|-----------------|  
|[SCRIPTTHREADID 常數](../../winscript/reference/scriptthreadid-constants.md)|指定執行緒的類型。|  
  
## <a name="properties"></a>屬性  
  
|屬性|描述|  
|--------------|-----------------|  
|[SCRIPTPROP_HOSTKEEPALIVE 屬性](../../winscript/reference/scriptprop-hostkeepalive-property.md)|用來指定應該保留指令碼引擎有未完成的參考的完整功能。|  
  
## <a name="enumerations"></a>列舉  
  
|列舉|描述|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE 列舉](../../winscript/reference/scriptgctype-enumeration.md)|若要執行記憶體回收的類型。|  
|[SCRIPTLANGUAGEVERSION 列舉](../../winscript/reference/scriptlanguageversion-enumeration.md)|指定可能的指令碼版本。|  
|[SCRIPTSTATE 列舉](../../winscript/reference/scriptstate-enumeration.md)|指定指令碼引擎的狀態。|  
|||  
|[SCRIPTTHREADSTATE 列舉](../../winscript/reference/scriptthreadstate-enumeration.md)|指定在指令碼引擎的執行緒的狀態。|  
|[SCRIPTTRACEINFO 列舉](../../winscript/reference/scripttraceinfo-enumeration.md)|表示所追蹤的指令碼事件。 用於[iactivescriptsitetraceinfo:: Sendscripttraceinfo 方法](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)。|  
|[SCRIPTUICHANDLING 列舉](../../winscript/reference/scriptuichandling-enumeration.md)|表示應該處理 UI 控制項的方式。|  
|[SCRIPTUICITEM 列舉](../../winscript/reference/scriptuicitem-enumeration.md)|表示 UI 項目類型。 用於[iactivescriptsiteuicontrol:: Getuibehavior 方法](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md)。|  
  
## <a name="error-codes"></a>錯誤碼  
  
|錯誤碼|描述|  
|----------------|-----------------|  
|[SCRIPT_E_PROPAGATE 錯誤碼](../../winscript/reference/script-e-propagate-error-code.md)|指令碼錯誤傳播給呼叫者，這可能是在不同的執行緒。|  
|[SCRIPT_E_RECORDED 錯誤碼](../../winscript/reference/script-e-recorded-error-code.md)|指令碼引擎和主機之間已傳遞錯誤。|  
|[SCRIPT_E_REPORTED 錯誤碼](../../winscript/reference/script-e-reported-error-code.md)|指令碼引擎回報至主應用程式處理的例外狀況。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼介面](../../winscript/reference/active-script-interfaces.md)