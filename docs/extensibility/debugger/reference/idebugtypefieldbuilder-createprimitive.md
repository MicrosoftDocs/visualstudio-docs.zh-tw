---
title: IDebugTypeFieldBuilder::CreatePrimitive |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- CreatePrimitive
- IDebugTypeFieldBuilder::CreatePrimitive
ms.assetid: 512c6ff0-97c5-409f-939f-4cc969bc4bb9
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 79adff9a94258ff3ebb1102763ddf417f79149a3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868316"
---
# <a name="idebugtypefieldbuildercreateprimitive"></a>IDebugTypeFieldBuilder::CreatePrimitive
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

建立表示基本類型的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in]值從[CorElementType 列舉](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration)表示基本類型。  
  
 `pTypeField`  
 [out]傳回新類型的 IDebugField 介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)
