---
title: IDebugSymbolProvider::GetAddressesFromPosition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b354c7c31f4633fd307f54954c5d5115436097d0
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66207353"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
這個方法會對應到陣列的文件位置的偵錯位址。

## <a name="syntax"></a>語法

```cpp
HRESULT GetAddressesFromPosition( 
   IDebugDocumentPosition2* pDocPos,
   BOOL                     fStatmentOnly,
   IEnumDebugAddresses**    ppEnumBegAddresses,
   IEnumDebugAddresses**    ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromPosition( 
   IDebugDocumentPosition2  pDocPos,
   bool                     fStatmentOnly,
   out IEnumDebugAddresses  ppEnumBegAddresses,
   out IEnumDebugAddresses  ppEnumEndAddresses
);
```

## <a name="parameters"></a>參數
`pDocPos`\
[in]文件位置。

`fStatmentOnly`\
[in]如果為 TRUE，會限制單一陳述式的偵錯位址。

`ppEnumBegAddresses`\
[out]傳回與這個陳述式或列關聯的開始偵錯位址的列舉值。

`ppEnumEndAddresses`\
[out]傳回[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)結束此陳述式或列相關聯的偵錯地址的列舉值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 文件位置通常表示一組原始程式行。 此方法可讓您提供的開始和結束偵錯位址相關聯這幾行。 有些語言允許跨越多行或包含多個陳述式的行的陳述式。 這個方法會提供要限制為單一陳述式的偵錯位址的旗標。

 可以單一的陳述式，才會有多個偵錯位址，如同範本的情況。

## <a name="see-also"></a>另請參閱
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)