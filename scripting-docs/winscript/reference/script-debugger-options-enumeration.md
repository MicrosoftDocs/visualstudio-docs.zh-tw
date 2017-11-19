---
title: "SCRIPT_DEBUGGER_OPTIONS 列舉 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54b910562670104f0fb5679f2b09780afcd17751
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="scriptdebuggeroptions-enumeration"></a>SCRIPT_DEBUGGER_OPTIONS 列舉
表示一組選項及/或套用至附加偵錯工具的功能。 用於[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)和[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  這些常數會實作由 PDM v10.0 和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```  
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>成員  
  
|成員|值|描述|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|未設定選項。|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|表示指令碼執行階段應該引發 BREAKREASON_ERROR 事件時擲回例外狀況。 這個選項可能偵錯工具，來設定或設定由使用者程式碼透過`Debug.enableFirstChanceExceptions(<true&#124;false>)`。|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|指出附加偵錯工具支援 web 背景工作。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)