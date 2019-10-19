---
title: IApplicationDebugger：： onDebugOutput |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onDebugOutput
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onDebugOutput
ms.assetid: 978d8bcf-16dc-4f24-a6bc-206adee2b2e9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ebbb7fb9f69af2f0977434a29015d79e8cf9178
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577852"
---
# <a name="iapplicationdebuggerondebugoutput"></a>IApplicationDebugger::onDebugOutput
處理 debug 輸出事件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT onDebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstr`  
 在要在偵錯工具中顯示的字串。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 偵錯工具通常會在 [輸出] 視窗中顯示 `pstr`。  
  
 呼叫 `IDebugApplication::DebugOutput` 時，會呼叫這個方法。  
  
## <a name="see-also"></a>請參閱  
 [IApplicationDebugger 介面](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)