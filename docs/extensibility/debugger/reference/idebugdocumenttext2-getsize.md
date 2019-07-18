---
title: IDebugDocumentText2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7f382b1d27a83e4493431ac8e6cca3d6aef9dd72
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337382"
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

## <a name="parameters"></a>參數
`pcNumLines`\
[out]傳回的文字行數。

`pcNumChars`\
[out]傳回文字的字元數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註

 [C++只]如果不需要特定的值，傳遞參數為 NULL。

 [C#只]必須指定這兩個參數。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)