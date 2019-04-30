---
title: IActiveScriptSite::GetLCID | Microsoft Docs
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
ms.openlocfilehash: c6ebcfec9764aae98f7d74ac98e0c88ecec7c4da
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992771"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
擷取主機的使用者介面相關聯的地區設定識別碼。 指令碼引擎會使用識別碼，以確保錯誤字串及其他引擎所產生的使用者介面項目會出現在適當的語言。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>參數  
 `plcid`  
 [out]接收指令碼引擎所顯示的使用者介面元素的地區設定識別碼的變數位址。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|這個方法尚未實作。 使用系統定義的地區設定。|  
|`E_POINTER`|指定了無效的指標。|  
  
## <a name="remarks"></a>備註  
 如果此方法傳回`E_NOTIMPL`，應該使用系統定義的地區設定識別碼。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)