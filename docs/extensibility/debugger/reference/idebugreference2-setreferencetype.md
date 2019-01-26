---
title: IDebugReference2::SetReferenceType |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugReference2::SetReferenceType
helpviewer_keywords:
- IDebugReference2::SetReferenceType
ms.assetid: 5854a172-ea82-481c-97d9-c7fc16923d44
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c73ef6fb192f1b2e5538a3ad020147a6d8836678
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021607"
---
# <a name="idebugreference2setreferencetype"></a>IDebugReference2::SetReferenceType
設定參考型別。 保留供未來使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetReferenceType (   
   REFERENCE_TYPE dwRefType  
);  
```  
  
```csharp  
int SetReferenceType (   
   enum_REFERENCE_TYPE dwRefType  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwRefType`  
 [in]值，以從[REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)列舉，指定參考型別。  
  
## <a name="return-value"></a>傳回值  
 一律傳回 `E_NOTIMPL`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)