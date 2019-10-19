---
title: IActiveScriptSite：： GetDocVersionString |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ecc592b6b7fcae5f516a3c1dd111c027e67b6dc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571127"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
抓取可唯一識別目前檔版本的主機定義字串。 如果相關檔在 Windows 腳本範圍外已變更（例如，使用 [記事本] 編輯 HTML 網頁的情況），則腳本引擎可以將其儲存在其保存的狀態下，並在下次載入腳本時強制重新編譯。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrVersionString`  
 脫銷主機定義之檔版本字串的位址。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`，如果不支援這個方法，則傳回 `E_NOTIMPL`。  
  
## <a name="remarks"></a>備註  
 如果傳回 `E_NOTIMPL`，腳本引擎應該會假設腳本與檔同步。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)