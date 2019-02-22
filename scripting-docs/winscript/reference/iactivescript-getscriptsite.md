---
title: IActiveScript::GetScriptSite |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptSite
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85b7d94ccb9e2589b10bf705721fc289df9638a9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094155"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
擷取與 Windows 指令碼引擎相關聯的站台物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>參數  
 `iid`  
 [in]要求的介面識別碼。  
  
 `ppvSiteObject`  
 [out]接收主機的站台物件的介面指標的位置的位址。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_NOINTERFACE`|不支援指定的介面。|  
|`E_POINTER`|指定了無效的指標。|  
|`S_FALSE`|不是站台已設定;`ppvSiteObject`參數設為`NULL`。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)