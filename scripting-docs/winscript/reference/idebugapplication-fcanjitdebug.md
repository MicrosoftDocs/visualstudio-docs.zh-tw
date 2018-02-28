---
title: "IDebugApplication::FCanJitDebug |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.FCanJitDebug
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FCanJitDebug
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ca6b990011252bde581168a272da1041dc24f41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationfcanjitdebug"></a>IDebugApplication::FCanJitDebug
判斷是否已登錄在 just-in-time (JIT) 偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```  
BOOL FCanJitDebug();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會採用任何參數。  
  
## <a name="return-value"></a>傳回值  
 如果此方法成功，而且已註冊的 JIT 偵錯工具，方法會傳回`TRUE`。 否則它會傳回 `FALSE`。  
  
## <a name="remarks"></a>備註  
 這個方法會判斷是否已登錄 JIT 偵錯工具。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)