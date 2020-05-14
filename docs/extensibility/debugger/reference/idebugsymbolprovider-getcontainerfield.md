---
title: IDebugSymbol提供程式:獲取容器欄位 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetContainerField
helpviewer_keywords:
- IDebugSymbolProvider::GetContainerField method
ms.assetid: d6b56b4f-a96b-4fa7-87c1-bac4e58fa766
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 729457fd071ab4a271f46b159e031fdc5cfc19bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719390"
---
# <a name="idebugsymbolprovidergetcontainerfield"></a>IDebugSymbolProvider::GetContainerField
此方法獲取包含調試位址的欄位。

## <a name="syntax"></a>語法

```cpp
HRESULT GetContainerField( 
   IDebugAddress*         pAddress,
   IDebugContainerField** ppContainerField
);
```

```csharp
int GetContainerField(
   IDebugAddress            pAddress,
   out IDebugContainerField ppContainerField
);
```

## <a name="parameters"></a>參數
`pAddress`\
[在]由[IDebug 位址](../../../extensibility/debugger/reference/idebugaddress.md)介面表示的位址。

`ppContainerField`\
[出]返回由[IDebug 容器欄位](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面表示的容器欄位。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
