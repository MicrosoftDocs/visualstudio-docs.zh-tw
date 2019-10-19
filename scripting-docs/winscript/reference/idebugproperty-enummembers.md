---
title: IDebugProperty：： EnumMembers |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f8c5f2cbb107d55e9ffe602cb7d3492701de10c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562414"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
列舉屬性的成員。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFieldSpec`  
 在指定 `DBGPROP_INFO_FLAGS` 常數，以決定要填入列舉的 debug 屬性結構中的哪些欄位。  
  
 `nRadix`  
 在用來解讀任何數值資訊的基數。  
  
 `refiid`  
 在傳遞這個 IID 來篩選列舉值。 IID 是繼承自 `IDebugPropertyEnumType_All` 的其中一個 `IDebugPropertyEnumType` 介面。  
  
 `ppEnum`  
 脫銷傳回列舉成員屬性的 `IEnumDebugPropertyInfo` 介面。  
  
## <a name="return-value"></a>傳回值  
 傳回有效的 `HRESULT`，通常是 `S_OK`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)    
 [IDebugPropertyEnumType_All 介面](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [IEnumDebugPropertyInfo 介面](../../winscript/reference/ienumdebugpropertyinfo-interface.md)