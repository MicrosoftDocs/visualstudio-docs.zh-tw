---
title: IDebugDocumentText2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3d5749a4bd738d6ec7edbf926542dbde0eb59db6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685543"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
擷取文件中的這個位置的文字的大小。

## <a name="syntax"></a>語法

```cpp
HRESULT GetSize( 
   ULONG* pcNumLines,
   ULONG* pcNumChars
);
```

```csharp
int GetSize( 
   ref uint pcNumLines,
   ref uint pcNumChars
);
```

#### <a name="parameters"></a>參數
 `pcNumLines`

 [out]傳回的文字行數。

 `pcNumChars`

 [out]傳回文字的字元數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註

 [只有 c + +]如果不需要特定的值，傳遞參數為 NULL。


 [C#只]必須指定這兩個參數。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)