---
title: IDebugApplicationThreadEvents110::OnSuspendForBreakPoint |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
ms.assetid: 224245ac-2aa2-43ae-97ed-493afc3d0122
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9e39af9784b139e935c271fca6db565136352cf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440426"
---
# <a name="idebugapplicationthreadevents110onsuspendforbreakpoint"></a>IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
判斷執行緒是否具有完整的停用中斷點，並還沒有已恢復正常執行。  
  
> [!IMPORTANT]
> [IDebugApplicationThreadEvents110 介面](../../winscript/reference/idebugapplicationthreadevents110-interface.md)是實作由 PDM v11.0 和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OnSuspendForBreakPoint( void );  
```  
  
#### <a name="parameters"></a>參數  
 這個方法沒有任何參數。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationThreadEvents110 介面](../../winscript/reference/idebugapplicationthreadevents110-interface.md)