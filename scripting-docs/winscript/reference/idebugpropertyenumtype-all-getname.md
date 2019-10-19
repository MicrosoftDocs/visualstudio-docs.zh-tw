---
title: IDebugPropertyEnumType_All：： GetName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All::GetName
ms.assetid: 24bbe4d5-4263-48d0-8e8d-bff957ffcad2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad5d8d1d1b9e2e7ee632ed3fec40b89df5b4bc07
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577378"
---
# <a name="idebugpropertyenumtype_allgetname"></a>IDebugPropertyEnumType_All::GetName
傳回包含 `EnumType` 名稱的 BSTR。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetName(  
   BSTR*  pname  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pname`  
 脫銷包含 `EnumType` 名稱的 BSTR。  
  
## <a name="return-value"></a>傳回值  
 傳回有效的 `HRESULT`，通常是 `S_OK`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugPropertyEnumType_All Interface](../../winscript/reference/idebugpropertyenumtype-all-interface.md)