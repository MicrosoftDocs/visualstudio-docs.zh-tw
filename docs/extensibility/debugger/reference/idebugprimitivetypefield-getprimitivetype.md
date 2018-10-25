---
title: IDebugPrimitiveTypeField::GetPrimitiveType |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetPrimitiveType
- IDebugPrimitiveTypeField::GetPrimitiveType
ms.assetid: a186c922-bbfe-478c-a744-b21eb4672d8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c1c847bb8ab7b347cf60b8bb4035d2db709d529
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899483"
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
 [out]值從[CorElementType 列舉](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration)表示基本類型。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)