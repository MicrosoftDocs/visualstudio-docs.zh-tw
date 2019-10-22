---
title: ExtendedDebugPropertyInfo 結構 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09f3c5a219fca9ec9b881e2ae8363aae4d48e03f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575841"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo 結構
使用其他成員擴充 `DebugPropertyInfo` 結構，以描述擴充屬性的特性。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>Members  
 `dwValidFields`  
 列舉的資料類型，用來指定要初始化的欄位。  
  
 `bstrName`  
 內容中的屬性名稱。  
  
 `bstrType`  
 格式化字串形式的屬性類型。  
  
 `bstrValue`  
 格式化字串形式的屬性值。  
  
 `bstrFullName`  
 屬性的完整名稱。  
  
 `dwAttrib`  
 列舉，指定 debug 屬性屬性的旗標。  
  
 `pDebugProp`  
 與這個 `ExtendedDebugPropertyInfo` 對應的 `IDebugProperty` 物件。  
  
 `nDISPID`  
 分派識別碼。  
  
 `nType`  
 擴充屬性類型。  
  
 `varValue`  
 擴充屬性值（如果可以放入 VARIANT 中）。  
  
 `plbValue`  
 屬性值的實際資料位元組。  
  
 `pDebugExtProp`  
 與這個 `ExtendedDebugPropertyInfo` 對應的 `IDebugExtendedProperty` 物件。  
  
## <a name="see-also"></a>請參閱  
 [DebugPropertyInfo 結構](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty 介面](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)    
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)