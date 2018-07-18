---
title: DebugStackFrameDescriptor 結構 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 346f039ca96f2160d7ac28686e542b3d88a91dfb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641128"
---
# <a name="debugstackframedescriptor-structure"></a>DebugStackFrameDescriptor 結構
會列舉堆疊框架並合併相同執行緒上數個列舉值的輸出。  
  
## <a name="syntax"></a>語法  
  
```  
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
 較低的範圍，此堆疊框架相關聯的實體位址的電腦相關表示法。  
  
 `dwLim`  
 電腦相關的表示此堆疊框架相關聯的實體位址的上限範圍。  
  
 `fFinal`  
 表示正在處理之框架的旗標。  
  
 `punkFinal`  
 如果這個參數不是`NULL`時，應該停止合併目前的列舉值，應該啟動新的。 物件表示如何啟動新的列舉型別。  
  
## <a name="remarks"></a>備註  
 處理序偵錯管理員會使用此結構來分類從多個指令碼引擎的堆疊框架。 依照慣例，堆疊成長下。 因此，在其中堆疊成長的架構位址應該並補充。  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)