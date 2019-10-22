---
title: IActiveScriptSite：： GetLCID |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 913ca23ac687fdd080a778afb1dcba2e4dcdd6b8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570734"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
抓取與主機的使用者介面相關聯的地區設定識別碼。 腳本引擎會使用識別碼，以確保引擎產生的錯誤字串和其他使用者介面元素會以適當的語言顯示。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>參數  
 `plcid`  
 脫銷此變數的位址會接收腳本引擎所顯示之使用者介面元素的地區設定識別碼。  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|這個方法尚未實作。 使用系統定義的地區設定。|  
|`E_POINTER`|指定了不正確指標。|  
  
## <a name="remarks"></a>備註  
 如果這個方法傳回 `E_NOTIMPL`，就應該使用系統定義的地區設定識別碼。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)