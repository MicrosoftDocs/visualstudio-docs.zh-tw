---
title: IDebugCodeCoNtext：： SetBreakPoint |Microsoft Docs
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
ms.openlocfilehash: df2bb0395cc1aeaceda3763b2c4016bbd9ba7e1f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573203"
---
# <a name="idebugcodecontextsetbreakpoint"></a>IDebugCodeContext::SetBreakPoint
設定或清除此程式碼內容中的中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bps`  
 在指定此程式碼內容的中斷點狀態。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會在此程式碼內容中設定或清除中斷點。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCodeCoNtext 介面](../../winscript/reference/idebugcodecontext-interface.md)   
 [BREAKPOINT_STATE 列舉](../../winscript/reference/breakpoint-state-enumeration.md)