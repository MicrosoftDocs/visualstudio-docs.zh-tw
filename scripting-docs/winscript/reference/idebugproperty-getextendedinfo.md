---
title: IDebugProperty::GetExtendedInfo |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6dc3fc90b8f5fa465715bc4b9466da472cbbb580
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086537"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
取得擴充屬性的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cInfos`  
 [in]擴充的資訊物件的計數。  
  
 `rgguidExtendedInfo`  
 [in]陣列`GUID`s 傳遞，因此可以同時擷取的擴充資訊的多個項目。  
  
 `pExtendedInfo`  
 [out]傳回的陣列`VARIANT`，它可用來擷取擴充的屬性的資訊。  
  
## <a name="return-value"></a>傳回值  
 會傳回有效`HRESULT`，通常是`S_OK`。  
  
## <a name="remarks"></a>備註  
 這個介面取得擴充這個物件的資訊。 API 存在的唯一理由擷取本身就無法使用所擷取的資訊`IDebugProperty::GetPropertyInfo`)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)