---
title: IJsDebugProcess：： CreateBreakPoint 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateBreakPoint
apilocation:
- jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b0a4d595a11dc54829c467a0aace9601042fa08
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575097"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint 方法
在指定的檔位置設定中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>參數  
 `documentId`  
 在IDebugDocumentText 的指標。  
  
 `characterOffset`  
 在檔案開頭的字元位移。  
  
 `characterCount`  
 在應在其中插入中斷點之檔文字的長度。  
  
 `isEnabled`  
 在指定中斷點是否已啟用。  
  
 `ppDebugBreakPoint`  
 脫銷物件，代表已建立的中斷點。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IJsDebugProcess 介面](../../winscript/reference/ijsdebugprocess-interface.md)