---
title: IDebugProperty：： GetExtendedInfo |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 130d11c8ed6bb21210d129bb9aace779db3bd54b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562399"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
取得屬性的擴充資訊。  
  
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
 在擴充資訊物件的計數。  
  
 `rgguidExtendedInfo`  
 在傳遞了 `GUID`s 的陣列，因此可以同時抓取擴充資訊的多個專案。  
  
 `pExtendedInfo`  
 脫銷傳回可用於抓取擴充屬性資訊的 `VARIANT`s 陣列。  
  
## <a name="return-value"></a>傳回值  
 傳回有效的 `HRESULT`，通常是 `S_OK`。  
  
## <a name="remarks"></a>備註  
 這個介面會取得此物件的延伸資訊。 應用程式開發介面的目的，只是為了取得無法透過使用 `IDebugProperty::GetPropertyInfo` 來取得本身的資訊。  
  
## <a name="see-also"></a>請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)