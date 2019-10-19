---
title: 動態指令碼常數、列舉和錯誤碼 |Microsoft Docs
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
ms.openlocfilehash: e03bef99c2297d517aa5234db49820a2b9600ce7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572717"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>動態指令碼的常數、列舉和錯誤碼
本節說明 Windows 腳本引擎中使用的列舉和錯誤碼。  
  
## <a name="constants"></a>常數  
  
|常數|描述|  
|--------------|-----------------|  
|[SCRIPTTHREADID 常數](../../winscript/reference/scriptthreadid-constants.md)|指定執行緒的類型。|  
  
## <a name="properties"></a>內容  
  
|屬性|描述|  
|--------------|-----------------|  
|[SCRIPTPROP_HOSTKEEPALIVE 屬性](../../winscript/reference/scriptprop-hostkeepalive-property.md)|用來指定如果有未處理的參考，腳本引擎是否應該保持完整功能。|  
  
## <a name="enumerations"></a>列舉  
  
|列舉|描述|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE 列舉](../../winscript/reference/scriptgctype-enumeration.md)|要執行的垃圾收集類型。|  
|[SCRIPTLANGUAGEVERSION 列舉](../../winscript/reference/scriptlanguageversion-enumeration.md)|指定可能的腳本版本。|  
|[SCRIPTSTATE 列舉](../../winscript/reference/scriptstate-enumeration.md)|指定腳本引擎的狀態。|  
|||  
|[SCRIPTTHREADSTATE 列舉](../../winscript/reference/scriptthreadstate-enumeration.md)|指定腳本引擎中的執行緒狀態。|  
|[SCRIPTTRACEINFO 列舉](../../winscript/reference/scripttraceinfo-enumeration.md)|表示正在追蹤的腳本事件。 用於[IActiveScriptSiteTraceInfo：： SendScriptTraceInfo 方法](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)中。|  
|[SCRIPTUICHANDLING 列舉](../../winscript/reference/scriptuichandling-enumeration.md)|表示 UI 控制項的處理方式。|  
|[SCRIPTUICITEM 列舉](../../winscript/reference/scriptuicitem-enumeration.md)|表示 UI 專案的類型。 用於[IActiveScriptSiteUIControl：： GetUIBehavior 方法](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md)中。|  
  
## <a name="error-codes"></a>錯誤碼  
  
|錯誤碼|描述|  
|----------------|-----------------|  
|[SCRIPT_E_PROPAGATE 錯誤碼](../../winscript/reference/script-e-propagate-error-code.md)|腳本錯誤已傳播至呼叫端，可能在不同的執行緒中。|  
|[SCRIPT_E_RECORDED 錯誤碼](../../winscript/reference/script-e-recorded-error-code.md)|腳本引擎與主機之間已傳遞錯誤。|  
|[SCRIPT_E_REPORTED 錯誤碼](../../winscript/reference/script-e-reported-error-code.md)|腳本引擎已向主機回報未處理的例外狀況。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼介面](../../winscript/reference/active-script-interfaces.md)