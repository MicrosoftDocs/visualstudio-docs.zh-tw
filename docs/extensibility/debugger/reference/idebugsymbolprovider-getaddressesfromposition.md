---
title: IDebugSymbolProvider：： GetAddressesFromPosition |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15838ff1efe9cba6920b98a8b7f00cb62f2fc3b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956460"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
這個方法會將檔位置對應到一個 debug 位址陣列中。

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
在檔位置。

`fStatmentOnly`\
在若為 TRUE，則會將 debug 位址限制為單一語句。

`ppEnumBegAddresses`\
擴展傳回與這個語句或行相關聯之起始偵錯工具位址的列舉值。

`ppEnumEndAddresses`\
擴展傳回與這個語句或行相關之結束 debug 位址的 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) 列舉值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 檔位置通常表示原始程式列的範圍。 這個方法會提供與這些行相關聯的開始與結束的偵錯工具位址。 某些語言允許跨越多行的語句，或是包含多個語句的行。 這個方法會提供旗標，將 debug 位址限制為單一語句。

 單一語句有可能會有多個 debug 位址，如同範本的情況一樣。

## <a name="see-also"></a>另請參閱
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
