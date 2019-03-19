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
ms.openlocfilehash: 0862e6fc670be6cd3d3ca9fbf67f453aa0772a90
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158980"
---
# <a name="appbreakflags-enumeration"></a>APPBREAKFLAGS 列舉
指出應用程式和執行緒的目前偵錯狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>成員  
  
|成員|值|描述|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|語言引擎應立即中斷所有執行緒上使用 BREAKREASON_DEBUGGER_BLOCK。|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|語言引擎應立即中斷與 BREAKREASON_DEBUGGER_HALT。|  
|APPBREAKFLAG_STEP|0x00010000|語言引擎應立即中斷與 BREAKREASON_STEP 逐步執行的執行緒中。|  
|APPBREAKFLAG_NESTED|0x00020000|應用程式是在中斷點上的巢狀執行中。|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|偵錯工具會逐步執行來源層級。|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|偵錯工具會逐步執行位元組程式碼層級。|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|偵錯工具會逐步執行電腦層級。|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|遮罩析出步驟類型。|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|中斷點是在進行中。|  
  
## <a name="remarks"></a>備註  
 某些旗標會指定其他旗標會指定偵錯工具逐步執行模式時，應該在下次有機會，分頁語言引擎。  
  
## <a name="see-also"></a>另請參閱  
 [作用中的指令碼偵錯工具的常數、 列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON 列舉](../../winscript/reference/breakreason-enumeration.md)