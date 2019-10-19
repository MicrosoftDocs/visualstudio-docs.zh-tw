---
title: SCRIPT_DEBUGGER_OPTIONS 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c69d419732786442cda275bf85c74ab2b9d3e870
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574555"
---
# <a name="script_debugger_options-enumeration"></a>SCRIPT_DEBUGGER_OPTIONS 列舉
表示套用至附加偵錯工具的一組選項和（或）功能。 用於[IDebugApplicationNode100：： GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)和[IDebugApplicationNode100：： SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
> 這些常數是由 PDM 10.0 和更新版本所執行。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Members  
  
|成員|值|描述|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|未設定任何選項。|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|指出當擲回例外狀況時，腳本執行時間應該引發 BREAKREASON_ERROR 事件。 此選項可由偵錯工具設定，或透過 `Debug.enableFirstChanceExceptions(<true&#124;false>)` 由使用者程式碼設定。|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|指出附加的偵錯工具支援 web 背景工作。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)