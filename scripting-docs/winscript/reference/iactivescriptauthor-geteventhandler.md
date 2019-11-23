---
title: IActiveScriptAuthor：： GetEventHandler |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c69b32f0040ea6d52e0712b8e1813cc5a0b40c58
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576222"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
傳回具有指定屬性的程式碼片段。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
 在對應至程式碼片段附加之 `NamedItem` 的 `IDispatch` 物件。  
  
 `pszItem`  
 在主機中完整程式碼片段名稱的最上層識別碼的緩衝區位址。  
  
 `pszSubItem`  
 在主機中完整程式碼片段名稱的第二層識別碼的緩衝區位址。 如果名稱只有一個層級，則設定為 Null。  
  
 `pszEvent`  
 在包含事件名稱的緩衝區位址。 程式碼片段是此事件的事件處理常式。  
  
 `ppse`  
 脫銷此變數的位址，會接收具有指定屬性之程式碼片段的 `IScriptEntry` 介面的指標。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)