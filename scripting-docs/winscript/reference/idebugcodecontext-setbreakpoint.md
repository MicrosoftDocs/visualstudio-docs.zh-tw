---
title: IDebugCodeContext::SetBreakPoint |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCodeContext.SetBreakPoint
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugCodeContext::SetBreakPoint
ms.assetid: ecd42eae-66fa-40d3-9e47-08b826784108
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7bbfe38c1db9f7c9afff34f5a92b8c43b0f4f9ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974523"
---
# <a name="idebugcodecontextsetbreakpoint"></a>IDebugCodeContext::SetBreakPoint
設定或清除在本文中的程式碼中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bps`  
 [in]指定此程式碼內容 「 中斷點 」 狀態。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會設定或清除在本文中的程式碼中斷點。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCodeContext 介面](../../winscript/reference/idebugcodecontext-interface.md)   
 [BREAKPOINT_STATE 列舉](../../winscript/reference/breakpoint-state-enumeration.md)