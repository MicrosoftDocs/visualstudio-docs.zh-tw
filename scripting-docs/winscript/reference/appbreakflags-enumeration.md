---
title: APPBREAKFLAGS 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- APPBREAKFLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de6efbc20843fcaa73965334c18cf0e5c2a0abab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572657"
---
# <a name="appbreakflags-enumeration"></a>APPBREAKFLAGS 列舉
指出應用程式和執行緒的目前偵錯狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Members  
  
|成員|值|描述|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|語言引擎應該會在具有 BREAKREASON_DEBUGGER_BLOCK 的所有線程上立即中斷。|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|語言引擎應該會立即中斷 BREAKREASON_DEBUGGER_HALT。|  
|APPBREAKFLAG_STEP|0x00010000|語言引擎應該會在 BREAKREASON_STEP 的逐步執行執行緒中立即中斷。|  
|APPBREAKFLAG_NESTED|0x00020000|應用程式會在中斷點上進行嵌套的執行。|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|偵錯工具會在來源層級逐步執行。|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|偵錯工具會在位元組程式碼層級逐步執行。|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|偵錯工具會在機器層級逐步執行。|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|用來分解步驟類型的遮罩。|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|中斷點正在進行中。|  
  
## <a name="remarks"></a>備註  
 某些旗標指定語言引擎應該在下一個機會中斷，而其他旗標則指定偵錯工具的逐步執行模式。  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON 列舉](../../winscript/reference/breakreason-enumeration.md)