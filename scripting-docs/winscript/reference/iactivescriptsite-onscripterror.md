---
title: IActiveScriptSite：： OnScriptError |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptError
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f0078b53515a881d7f2ac1475cf5565fa22a025
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570265"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
當引擎執行腳本時，通知主機發生執行錯誤。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pase`  
 在錯誤物件的[IActiveScriptError](../../winscript/reference/iactivescripterror.md)介面位址。 主機可以使用此介面來取得有關執行錯誤的資訊。  
  
## <a name="return-value"></a>傳回值  
 如果錯誤已正確處理，則會傳回 `S_OK`，否則會傳回 OLE 定義的錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)