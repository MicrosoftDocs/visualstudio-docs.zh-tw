---
title: IScriptEntry::GetItemName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetItemName
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fc82dbd26fc2b9956b3d32596e5fa730b96f9a8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093453"
---
# <a name="iscriptentrygetitemname"></a>IScriptEntry::GetItemName
傳回項目名稱可識別`IScriptEntry`物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstr`  
 [out]包含的項目名稱的緩衝區位址。 項目名稱是主機用來識別項目。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 針對`IScriptScriptlet`物件，使用設定項目名稱[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)。 至於其他介面，您必須設定的項目名稱使用[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)