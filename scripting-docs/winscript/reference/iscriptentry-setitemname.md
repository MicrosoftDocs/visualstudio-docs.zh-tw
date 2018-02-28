---
title: "IScriptEntry::SetItemName |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 483d3cdc1c8b8de9342003a99427fc2c727ad67f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
設定識別的項目名稱`IScriptEntry`物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>參數  
 `psz`  
 [in]包含項目名稱的緩衝區位址。 項目名稱由主機用於識別項目。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|此方法失敗。|  
  
## <a name="remarks"></a>備註  
 如`IScriptEntry`物件，這個方法會傳回`S_OK`。  
  
 如`IScriptScriptlet`物件 (它衍生自`IScriptEntry`)，這個方法會傳回`E_FAIL`。 如`IScriptScriptlet`物件由所設定的項目名稱[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)且無法變更。  
  
## <a name="see-also"></a>另請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)