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
ms.openlocfilehash: fddae48178ec6c56ce647f5c4f3a1bff3d81a980
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955189"
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
  
## <a name="members"></a>成員  
 `pdsf`  
 堆疊框架物件。  
  
 `dwMin`  
 電腦相關的表示此堆疊框架相關聯的實體位址的較低的範圍。  
  
 `dwLim`  
 電腦相關的表示此堆疊框架相關聯的實體位址上限範圍。  
  
 `fFinal`  
 旗標，指出正在處理的框架。  
  
 `punkFinal`  
 如果此參數不是`NULL`，合併目前的列舉值應該停止，並且應該啟動新的。 物件表示如何啟動新的列舉型別。  
  
## <a name="remarks"></a>備註  
 處理序偵錯管理員會使用此結構來分類從多個指令碼引擎的堆疊框架。 依照慣例，堆疊會向下成長。 因此，在架構上堆疊會增加，位址應為成對輔助。  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)