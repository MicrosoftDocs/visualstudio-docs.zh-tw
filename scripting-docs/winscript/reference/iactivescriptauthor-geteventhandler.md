---
title: "IActiveScriptAuthor::GetEventHandler |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetEventHandler
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b09f900162b6dba82696c946b53ab131691530c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
傳回具有指定的屬性的程式碼片段。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdisp`  
 [in]`IDispatch`物件對應於`NamedItem`来附加的程式碼片段。  
  
 `pszItem`  
 [in]在主機中的完整程式碼片段名稱的最上層的識別項的緩衝區位址。  
  
 `pszSubItem`  
 [in]在主機中的完整程式碼片段名稱的第二個層級識別碼緩衝區位址。 如果只有一個層級名稱，請設為 NULL。  
  
 `pszEvent`  
 [in]包含事件名稱的緩衝區位址。 程式碼片段是此事件的事件處理常式。  
  
 `ppse`  
 [out]收到的指標變數的位址`IScriptEntry`介面的程式碼片段具有指定的屬性。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)