---
title: IDebugTypeFieldBuilder::CreatePrimitive |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CreatePrimitive
- IDebugTypeFieldBuilder::CreatePrimitive
ms.assetid: 512c6ff0-97c5-409f-939f-4cc969bc4bb9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8b855eea883bc17ee61b877087ddb176d1eb656
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugtypefieldbuildercreateprimitive"></a>IDebugTypeFieldBuilder::CreatePrimitive
建立表示基本類型的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreatePrimitive (  
   DWORD          dwElementType,  
   IDebugField ** pTypeField  
);  
```  
  
```csharp  
int CreatePrimitive (  
   uint            dwElementType,  
   out IDebugField pTypeField  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwElementType`  
 [in]從值[CorElementType 列舉](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration)表示基本類型。  
  
 `pTypeField`  
 [out]傳回新類型的 IDebugField 介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)