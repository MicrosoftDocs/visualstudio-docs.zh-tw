---
title: "IDebugPrimitiveTypeField::GetPrimitiveType |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetPrimitiveType
- IDebugPrimitiveTypeField::GetPrimitiveType
ms.assetid: a186c922-bbfe-478c-a744-b21eb4672d8f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3cba27320cd633c3f98ee01ec09cd2b8efbb3a45
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprimitivetypefieldgetprimitivetype"></a>IDebugPrimitiveTypeField::GetPrimitiveType
擷取這個欄位相關聯的基本類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPrimitiveType (  
   DWORD* pdwType  
);  
```  
  
```csharp  
int GetPrimitiveType (  
   out uint pdwType  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwType`  
 [out]從值[CorElementType 列舉](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration)表示基本類型。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)