---
title: IScriptEntry::SetItemName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20af0975a4175d10b110ac5e3cef9e0055f4ce1b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097756"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
設定項目名稱可識別`IScriptEntry`物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>參數  
 `psz`  
 [in]包含的項目名稱的緩衝區位址。 項目名稱是主機用來識別項目。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|不成功的方法。|  
  
## <a name="remarks"></a>備註  
 針對`IScriptEntry`物件，這個方法會傳回`S_OK`。  
  
 針對`IScriptScriptlet`物件 (這是衍生自`IScriptEntry`)，這個方法會傳回`E_FAIL`。 針對`IScriptScriptlet`物件，此項目的名稱由設定[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)且無法變更。  
  
## <a name="see-also"></a>另請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)