---
title: IDebugApplicationThread110::IsSuspendedForBreakPoint |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 5885f6a01ab09ef2d21277c875ff700712cc00fb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349592"
---
# <a name="idebugapplicationthread110issuspendedforbreakpoint"></a>IDebugApplicationThread110::IsSuspendedForBreakPoint
決定是否[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)已在這個執行緒上呼叫，但尚未完成。  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)是實作由 PDM v11.0 和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsSuspendedForBreakPoint([out, annotation("_Out_")] BOOL * pfIsSuspended);  
```  
  
#### <a name="parameters"></a>參數  
 `pfIsSuspended`  
 [out]`true`如果執行緒已經暫止中斷點，否則`false`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)