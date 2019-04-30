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
ms.openlocfilehash: 9a0777cf42b9ed9412602cb34ed2d521deca1fb9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968668"
---
# <a name="jsnativeframe-structure"></a>JS_NATIVE_FRAME 結構
代表堆疊框架。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef struct {  
    UINT64 InstructionOffset;    UINT64 ReturnOffset;    UINT64 FrameOffset;    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## <a name="members"></a>成員  
 `InstructionOffset`  
 指令指標。  
  
 `ReturnOffset`  
 傳回的位址。  
  
 `FrameOffset`  
 框架指標。  
  
 `StackOffset`  
 堆疊指標。  
  
## <a name="remarks"></a>備註  
 `JS_NATIVE_FRAME`建構由`IJsStackFrameEnumerator`。  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)