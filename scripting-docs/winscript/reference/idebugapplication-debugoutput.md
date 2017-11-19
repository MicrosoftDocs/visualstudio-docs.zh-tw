---
title: "IDebugApplication::DebugOutput |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.DebugOutput
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::DebugOutput
ms.assetid: 6c02939c-3c2d-474a-ab15-49a37e22b4a7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfc956c7d2d65d20788a79c9f685e386aba97a80
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationdebugoutput"></a>IDebugApplication::DebugOutput
會顯示偵錯工具整合式的開發環境 (IDE) 所指定的字串。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstr`  
 [in]若要在偵錯工具中顯示的字串。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法可讓偵錯輸出支援特定語言的實作語言引擎。 字串，通常會顯示偵錯工具的 [輸出] 視窗中。  
  
 這個方法會導致`IApplicationDebugger::onDebugOutput`呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)