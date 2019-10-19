---
title: IDebugApplicationThread110：： IsSuspendedForBreakPoint |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsSuspendedForBreakPoint
ms.assetid: 60688222-557f-4a43-a19b-846cee393cd0
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0e70993b95ccffcf6041bb04f37af90667fc4fd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574463"
---
# <a name="idebugapplicationthread110issuspendedforbreakpoint"></a>IDebugApplicationThread110::IsSuspendedForBreakPoint
判斷是否已在這個執行緒上呼叫[IDebugApplicationThreadEvents110：： OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) ，而且尚未完成。  
  
> [!IMPORTANT]
> [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)是由 PDM 11.0 和更新版本所執行。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsSuspendedForBreakPoint([out, annotation("_Out_")] BOOL * pfIsSuspended);  
```  
  
#### <a name="parameters"></a>參數  
 `pfIsSuspended`  
 [out] `true` 如果已暫止中斷點的執行緒，則為，否則為 `false`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)