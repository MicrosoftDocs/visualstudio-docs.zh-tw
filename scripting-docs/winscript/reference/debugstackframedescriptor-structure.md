---
title: DebugStackFrameDescriptor 結構 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugStackFrameDescriptor
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 910e08ec6d9982354eb71b50d5e916917808f140
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576545"
---
# <a name="debugstackframedescriptor-structure"></a>DebugStackFrameDescriptor 結構
會列舉堆疊框架並合併相同執行緒上數個列舉值的輸出。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>Members  
 `pdsf`  
 堆疊框架物件。  
  
 `dwMin`  
 與這個堆疊框架相關聯之實體位址範圍較低的電腦相依標記法。  
  
 `dwLim`  
 與這個堆疊框架相關聯之實體位址上方範圍的電腦相依標記法。  
  
 `fFinal`  
 表示正在處理框架的旗標。  
  
 `punkFinal`  
 如果未 `NULL` 此參數，則目前的列舉值合併應該會停止，而且應該會啟動一個新的。 物件會指出如何開始新的列舉。  
  
## <a name="remarks"></a>備註  
 進程 debug manager 會使用這個結構，從多個腳本引擎排序堆疊框架。 依照慣例，堆疊會逐漸降低。 因此，在堆疊增加的架構上，位址應該是2補數。  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)