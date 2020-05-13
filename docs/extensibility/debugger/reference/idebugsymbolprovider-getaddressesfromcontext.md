---
title: IDebugSymbol 提供程式:從上下文獲取位址 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7cf7599cf0fc37c16467c29c2b432f1f58b172fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719428"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
此方法將文件上下文映射到調試位址陣列中。

## <a name="syntax"></a>語法

```cpp
HRESULT GetAddressesFromContext( 
   IDebugDocumentContext2* pDocContext,
   BOOL                    fStatmentOnly,
   IEnumDebugAddresses**   ppEnumBegAddresses,
   IEnumDebugAddresses**   ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromContext(
   IDebugDocumentContext2  pDocContext,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>參數
`pDocContext`\
[在]文檔上下文。

`fStatmentOnly`\
[在]如果為 TRUE,則將調試位址限制為單個語句。

`ppEnumBegAddresses`\
[出]返回與此語句或行關聯的起始調試位址的枚舉器。

`ppEnumEndAddresses`\
[出]返回與此語句或行關聯的結束調試位址的[IEnumDebug 位址](../../../extensibility/debugger/reference/ienumdebugaddresses.md)枚舉器。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 文檔上下文通常指示源行的範圍。 此方法提供與這些行關聯的開始和結束調試位址。 某些語言允許跨多行的語句或包含多個語句的行。 此方法提供一個標誌,用於將調試位址限制為單個語句。

 單個語句可以有多個調試位址,如範本。

## <a name="see-also"></a>另請參閱
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
