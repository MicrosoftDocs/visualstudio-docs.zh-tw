---
title: "IScriptEntry::SetSignature |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptEntry.SetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetSignature
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9ff480f8e5c3192a7e2b355d39825cc3a084370
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
設定類型資訊`IScriptEntry`函式物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pti`  
 [in]型別資訊。  
  
 `iMethod`  
 [in]中的方法索引`ITypeInfo`物件。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 使用設定類型資訊`IScriptEntry::SetSignature`或[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)。 根據內部函式表示的項目也可以產生型別資訊。  
  
## <a name="see-also"></a>另請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)