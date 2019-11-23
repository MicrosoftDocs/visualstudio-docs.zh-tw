---
title: IDebugExtendedProperty：： EnumExtendedMembers |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.EnumExtendedMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::EnumExtendedMembers
ms.assetid: 27cdb091-da4e-44d2-a631-31ae00468b98
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6fd225be9504254965eab77b912f50fb5c777e3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576396"
---
# <a name="idebugextendedpropertyenumextendedmembers"></a>IDebugExtendedProperty::EnumExtendedMembers
列舉擴充屬性的成員。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnumExtendedMembers(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   IEnumDebugExtendedPropertyInfo**  ppeepi  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFieldSpec`  
 在指定 EX_DBGPROP_INFO_FLAGS 常數，以決定要填入之列舉擴充偵錯工具屬性結構中的欄位。  
  
 `nRadix`  
 在用來解讀任何數值資訊的基數。  
  
 `ppeepi`  
 脫銷傳回列舉成員屬性的 `IEnumDebugExtendedPropertyInfo` 介面。  
  
## <a name="return-value"></a>傳回值  
 傳回有效的 `HRESULT`，通常是 `S_OK`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExtendedProperty 介面](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo 結構](../../winscript/reference/extendeddebugpropertyinfo-structure.md)