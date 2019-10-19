---
title: JS_NATIVE_FRAME 結構 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_NATIVE_FRAME
apilocation:
- jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0b624229a96cfc2a2d2044a926f45fa91a1c76c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571771"
---
# <a name="js_native_frame-structure"></a>JS_NATIVE_FRAME 結構
代表堆疊框架。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef struct {  
    UINT64 InstructionOffset;    UINT64 ReturnOffset;    UINT64 FrameOffset;    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## <a name="members"></a>Members  
 `InstructionOffset`  
 指令指標。  
  
 `ReturnOffset`  
 傳回位址。  
  
 `FrameOffset`  
 框架指標。  
  
 `StackOffset`  
 堆疊指標。  
  
## <a name="remarks"></a>備註  
 @No__t_1 會使用 `JS_NATIVE_FRAME` 結構。  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)