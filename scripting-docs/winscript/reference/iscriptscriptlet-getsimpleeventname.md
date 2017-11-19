---
title: "IScriptScriptlet:: GetSimpleEventName |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptScriptlet. GetSimpleEventName
apilocation: scrobj.dll
helpviewer_keywords: IScriptScriptlet::GetSimpleEventName
ms.assetid: 012eb555-b26c-4248-bbcc-fc30e6f2b308
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ec90d2ebdf58f60ba88b90a38830b5df329dead
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptscriptlet-getsimpleeventname"></a>IScriptScriptlet:: GetSimpleEventName
傳回程式碼片段相關聯的簡單事件名稱。 這是單一字詞名稱不包含任何空白字元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetSimpleEventName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstr`  
 [out]包含相關聯的簡單事件名稱的緩衝區`IScriptScriptlet`物件。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IScriptScriptlet 介面](../../winscript/reference/iscriptscriptlet-interface.md)