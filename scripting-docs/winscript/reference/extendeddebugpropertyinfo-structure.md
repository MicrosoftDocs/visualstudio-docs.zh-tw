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
ms.openlocfilehash: 1fe0eef00d2bf064a8a002925f4ba5607d36f31c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160468"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo 結構
擴充`DebugPropertyInfo`結構描述的擴充的屬性的其他成員。  
  
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
  
## <a name="members"></a>成員  
 `dwValidFields`  
 用來指定哪些欄位會初始化列舉的資料型別。  
  
 `bstrName`  
 在內容屬性名稱。  
  
 `bstrType`  
 為格式化的字串屬性型別。  
  
 `bstrValue`  
 為格式化的字串屬性值。  
  
 `bstrFullName`  
 屬性的完整名稱。  
  
 `dwAttrib`  
 列舉型別，指定偵錯屬性的屬性的旗標。  
  
 `pDebugProp`  
 `IDebugProperty` 物件對應至這個`ExtendedDebugPropertyInfo`。  
  
 `nDISPID`  
 分派識別碼。  
  
 `nType`  
 擴充的屬性的型別。  
  
 `varValue`  
 如果它可以放入變數擴充的屬性值。  
  
 `plbValue`  
 屬性值的實際資料的位元組。  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` 物件對應至這個`ExtendedDebugPropertyInfo`。  
  
## <a name="see-also"></a>另請參閱  
 [DebugPropertyInfo 結構](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty 介面](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)