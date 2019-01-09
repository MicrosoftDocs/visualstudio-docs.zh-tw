---
title: IActiveScriptAuthor::GetEventHandler |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2e7f6cc265815db4acd847270b28c3e744257fa0
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086680"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
傳回含有指定的屬性程式碼片段。  
  
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
 [in]`IDispatch`物件，對應至`NamedItem`附加程式碼片段。  
  
 `pszItem`  
 [in]最上層的識別項的主應用程式中的完整程式碼片段名稱的緩衝區位址。  
  
 `pszSubItem`  
 [in]第二個層級識別項的主應用程式中的完整程式碼片段名稱的緩衝區位址。 如果名稱有只有一個層級，請設為 NULL。  
  
 `pszEvent`  
 [in]包含事件名稱的緩衝區位址。 程式碼片段是此事件的事件處理常式。  
  
 `ppse`  
 [out]收到的指標變數的位址`IScriptEntry`含有指定的屬性程式碼片段的介面。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)