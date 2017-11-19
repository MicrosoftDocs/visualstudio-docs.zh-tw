---
title: "IDebugProperty::GetPropertyInfo |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugProperty.GetPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edd878419c6f2b4fd0f882a070d80c98a96eba56
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
取得值`IDebugProperty`方法或索引的屬性描述。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFields`  
 [in]指定`DBGPROP_INFO_FLAGS`常數，決定要中填寫欄位`DebugPropertyInfo`結構。  
  
 `nRadix`  
 [in]基數來格式化數字的任何資訊。  
  
 `pPropertyInfo`  
 [out]傳回`DebugPropertyInfo`結構描述屬性。  
  
## <a name="return-value"></a>傳回值  
 傳回有效`HRESULT`，通常`S_OK`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [DebugPropertyInfo 結構](../../winscript/reference/debugpropertyinfo-structure.md)