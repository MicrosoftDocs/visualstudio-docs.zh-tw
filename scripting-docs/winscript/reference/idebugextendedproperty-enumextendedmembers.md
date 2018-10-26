---
title: IDebugExtendedProperty::EnumExtendedMembers |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 400145cf3981b7266a796f66576eb12f979d2750
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949834"
---
# <a name="idebugextendedpropertyenumextendedmembers"></a>IDebugExtendedProperty::EnumExtendedMembers
列舉擴充屬性的成員。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumExtendedMembers(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   IEnumDebugExtendedPropertyInfo**  ppeepi  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFieldSpec`  
 [in]指定要填入判斷列舉中的欄位擴充偵錯屬性結構，EX_DBGPROP_INFO_FLAGS 常數。  
  
 `nRadix`  
 [in]用於解譯任何數字資訊的基數。  
  
 `ppeepi`  
 [out]傳回`IEnumDebugExtendedPropertyInfo`列舉的成員屬性的介面。  
  
## <a name="return-value"></a>傳回值  
 會傳回有效`HRESULT`，通常是`S_OK`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExtendedProperty 介面](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo 結構](../../winscript/reference/extendeddebugpropertyinfo-structure.md)