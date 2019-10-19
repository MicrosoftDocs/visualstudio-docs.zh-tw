---
title: BREAKPOINT_STATE 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKPOINT_STATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKPOINT_STATE enumeration
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c56a8b135a0aa9a4f8ddf91e146d4d64367bb2b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572643"
---
# <a name="breakpoint_state-enumeration"></a>BREAKPOINT_STATE 列舉
指出中斷點的狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|BREAKPOINT_DELETED|中斷點已不存在，但仍有其參考。|  
|BREAKPOINT_DISABLED|中斷點存在，但已停用。|  
|BREAKPOINT_ENABLED|中斷點存在且已啟用。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)