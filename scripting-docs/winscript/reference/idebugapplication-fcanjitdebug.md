---
title: IDebugApplication::FCanJitDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FCanJitDebug
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FCanJitDebug
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d5dc03d7d2511f5b50969c062104759e78fcf03
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159006"
---
# <a name="idebugapplicationfcanjitdebug"></a>IDebugApplication::FCanJitDebug
判斷是否已登錄在 just-in-time (JIT) 偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```cpp
BOOL FCanJitDebug();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，而且在註冊 JIT 偵錯工具，此方法會傳回`TRUE`。 否則，它會傳回 `FALSE`。  
  
## <a name="remarks"></a>備註  
 這個方法會判斷是否已登錄的 JIT 偵錯工具。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)