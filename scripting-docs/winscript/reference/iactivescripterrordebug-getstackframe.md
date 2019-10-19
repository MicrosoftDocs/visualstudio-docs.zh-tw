---
title: IActiveScriptErrorDebug：： GetStackFrame |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptErrorDebug.GetStackFrame
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptErrorDebug::GetStackFrame
ms.assetid: a6f43102-68c5-46f5-a4df-fa3aaf53a967
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8542f83f926ba1a993527baecd6d5b667671b041
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576313"
---
# <a name="iactivescripterrordebuggetstackframe"></a>IActiveScriptErrorDebug::GetStackFrame
提供對執行階段錯誤有效的堆疊框架。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetStackFrame(  
   IDebugStackFrame**  ppdsf  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppdsf`  
 脫銷錯誤的堆疊框架。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會提供對執行時間錯誤有效的堆疊框架。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptErrorDebug 介面](../../winscript/reference/iactivescripterrordebug-interface.md)